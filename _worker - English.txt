Here's the translation of the provided text to English:

```javascript
// @ts-ignore
import { connect } from 'cloudflare:sockets';

// How to generate your own UUID:
// [Windows] Press "Win + R", input cmd and run:  Powershell -NoExit -Command "[guid]::NewGuid()"
let userID = 'd342d11e-d424-4583-b36e-524ab1f0afa4';

const proxyIPs = ['cdn.xn--b6gac.eu.org', 'cdn-all.xn--b6gac.eu.org', 'workers.cloudflare.cyou'];

// if you want to use ipv6 or a single proxy IP, please add comment at this line and remove comment at the next line
let proxyIP = proxyIPs[Math.floor(Math.random() * proxyIPs.length)];
// use single proxy IP instead of random
// let proxyIP = 'cdn.xn--b6gac.eu.org';
// ipv6 proxy IP example remove comment to use
// let proxyIP = "[2a01:4f8:c2c:123f:64:5:6810:c55a]"

let dohURL = 'https://sky.rethinkdns.com/1:-Pf_____9_8A_AMAIgE8kMABVDDmKOHTAKg='; // https://cloudflare-dns.com/dns-query or https://dns.google/dns-query

if (!isValidUUID(userID)) {
	throw new Error('uuid is invalid');
}

export
``` 

(Note: Words like "พร็อกซีไอพี" translate to "proxy IP" in English.) Here is the translated text:

",
                        },
                    });
                }
                case `/${userID_Path}`: {
                    const config = getConfig(userID, request.headers.get('Host'));
                    return new Response(`${config}`, {
                        status: 200,
                        headers: {
                            "Content-Type": "text/html; charset=utf-8",
                        }
                    });
                };
                case `/sub/${userID_Path}`: {
                    const url = new URL(request.url);
                    const searchParams = url.searchParams;
                    const subConfig = createSub(userID, request.headers.get('Host'));
                    // Construct and return response object
                    return new Response(btoa(subConfig), {
                        status: 200,
                        headers: {
                            "Content-Type": "text/plain;charset=utf-8",
                        }
                    });
                };
                case `/bestip/${userID_Path}`: {
                    const headers = request.headers;
                    const url = `https://sub.xf.free.hr/auto?host=${request.headers.get('Host')}&uuid=${userID}&path=/`;
                    const bestSubConfig = await fetch(url, { headers: headers Here is the translation of the provided text into English:

```
Request, { redirect: 'manual' });
						// Check for 302 or 301 redirect status and return an error response
						if ([301, 302].includes(proxyResponse.status)) {
							return new Response(`Redirects to ${randomHostname} are not allowed.`, {
								status: 403,
								statusText: 'Forbidden',
							});
						}
						// Return the response from the proxy server
						return proxyResponse;
				}
			} else {
				return await วเลสOverWSHandler(request);
			}
		} catch (err) {
			/** @type {Error} */ let e = err;
			return new Response(e.toString());
		}
	},
};

export async function uuid_validator(request) {
	const hostname = request.headers.get('Host');
	const currentDate = new Date();

	const subdomain = hostname.split('.')[0];
	const year = currentDate.getFullYear();
	const month = String(currentDate.getMonth() + 1).padStart(2, '0');
	const day = String(currentDate.getDate()).padStart(2, '0');

	const formattedDate = `${year}-${month}-${day}`;
```

The text contains code comments in English and programming logic in JavaScript. Therefore, it doesn’t require translation into another language as the code itself is already in a context understood by English-speaking developers. Would you like assistance with something specific regarding this code? Here is the English translation of the provided text:

```javascript
[t, webSocket] = Object.values(webSocketPair);
webSocket.accept();

let address = '';
let portWithRandomLog = '';
let currentDate = new Date();
const log = (/** @type {string} */ info, /** @type {string | undefined} */ event) => {
    console.log(`[${currentDate} ${address}:${portWithRandomLog}] ${info}`, event || '');
};
const earlyDataHeader = request.headers.get('sec-websocket-protocol') || '';

const readableWebSocketStream = makeReadableWebSocketStream(webSocket, earlyDataHeader, log);

/** @type {{ value: import("@cloudflare/workers-types").Socket | null}}*/
let remoteSocketWapper = {
    value: null,
};
let udpStreamWrite = null;
let isDns = false;

// ws --> remote
readableWebSocketStream.pipeTo(new WritableStream({
    async write(chunk, controller) {
        if (isDns && udpStreamWrite) {
            return udpStreamWrite(chunk);
        }
        if (remoteSocketWapper.value) {
            const writer = remoteSocketWapper.value.writable.getWriter();
            await ...
```

(Note: The provided text appears to be a snippet of JavaScript code, which contains comments and function definitions rather than standard prose. The translation retains the code structure and terminology.) Here's the translation of the provided text to English:

---

The cf runtime has UDP support.
If (isDns) {
    const { write } = await handleUDPOutBound(webSocket, วเลสResponseHeader, log);
    udpStreamWrite = write;
    udpStreamWrite(rawClientData);
    return;
}
handleTCPOutBound(remoteSocketWapper, addressRemote, portRemote, rawClientData, webSocket, วเลสResponseHeader, log);
},
close() {
    log(`readableWebSocketStream is close`);
},
abort(reason) {
    log(`readableWebSocketStream is abort`, JSON.stringify(reason));
},
})).catch((err) => {
    log('readableWebSocketStream pipeTo error', err);
});

return new Response(null, {
    status: 101,
    webSocket: client,
});

/**
* Handles outbound TCP connections.
*
* @param {any} remoteSocket
* @param {string} addressRemote The remote address to connect to.
* @param {number} portRemote The remote port to connect to.
* @param {Uint8Array} rawClientData The raw client data to write.
* @param {import("@cloudflare/workers-types").WebSocket} webSocket The

---

Note: The text contains code snippets and some parts of it seem to be in a programming context, particularly JavaScript/TypeScript. There are also some non-English characters (like “วเลส”) that appear to be part of variable names or other elements in the code; these have been retained as they are, as they don't have a direct translation or context in the provided text. If you need help with specific terms or context, let me know! Here's the translation of the provided text into English:

```
// First write, normal is TLS client hello
    writer.releaseLock();
    return tcpSocket;
}

/**
 * Retries connecting to the remote address and port if the Cloudflare socket has no incoming data.
 * @returns {Promise<void>} A Promise that resolves when the retry is complete.
 */
async function retry() {
    const tcpSocket = await connectAndWrite(proxyIP || addressRemote, portRemote);
    tcpSocket.closed.catch(error => {
        console.log('retry tcpSocket closed error', error);
    }).finally(() => {
        safeCloseWebSocket(webSocket);
    });
    remoteSocketToWS(tcpSocket, webSocket, responseHeader, null, log);
}

const tcpSocket = await connectAndWrite(addressRemote, portRemote);

// When remoteSocket is ready, pass to WebSocket
// remote --> ws
remoteSocketToWS(tcpSocket, webSocket, responseHeader, retry, log);
}

/**
* Creates a readable stream from a WebSocket server, allowing for data to be read from the WebSocket.
* @param
```

Note: I've retained the context and some terms because they seem to be specific to the code functionality (like `tcpSocket`, `WebSocket`, etc.). Additionally, certain phrases like `พร็อกซีไอพี` and `วเลสResponseHeader` were kept as they might be specific variable names or objects and the translation may depend on context within the codebase or application. If you need those translated as well, please clarify! Here is the translation of the provided text into English:

```javascript
r(earlyDataHeader);
if (error) {
    controller.error(error);
} else if (earlyData) {
    controller.enqueue(earlyData);
}

pull(controller) {
    // if web socket can stop reading if the stream is full, we can implement backpressure
    // https://streams.spec.whatwg.org/#example-rs-push-backpressure
},

cancel(reason) {
    log(`ReadableStream was canceled, due to ${reason}`);
    readableStreamCancel = true;
    safeCloseWebSocket(webSocketServer);
}

return stream;
}

// https://xtls.github.io/development/protocols/วเลส.html
// https://github.com/zizifn/excalidraw-backup/blob/main/v2ray-protocol.excalidraw

/**
* Processes the วเลส header buffer and returns an object with the relevant information.
* @param {ArrayBuffer} วเลสBuffer The วเลส header buffer to process.
* @param {string} userID The user ID to validate against the UUID in the วเลส header.
* @returns {{
* hasError: boolean,
* message?: string,
* addressRemote?: string,
* 
```

Note: The text includes technical coding elements and specific references to web protocols and programming functions in JavaScript. The term "วเลส" appears to be a specific term that may remain untranslated depending on its context in the programming framework. The provided text appears to be a segment of JavaScript code rather than a standard prose text. The raw and context-specific terms like "uuids", "Buffer", "Uint8Array", and "command" hint that this is likely part of a networking protocol or data handling procedure in the code.

Here is an English translation of the variable names and comments, preserving the original code structure:

```javascript
) || uuids.length === 1 && slicedBufferString === uuids[0].trim();

console.log(`userID: ${slicedBufferString}`);

if (!isValidUser) {
    return {
        hasError: true,
        message: 'invalid user',
    };
}

const optLength = new Uint8Array(buffer.slice(17, 18))[0];
// Skip OPT for now

const command = new Uint8Array(
    buffer.slice(18 + optLength, 18 + optLength + 1)
)[0];

// 0x01 TCP
// 0x02 UDP
// 0x03 MUX
if (command === 1) {
    isUDP = false;
} else if (command === 2) {
    isUDP = true;
} else {
    return {
        hasError: true,
        message: `command ${command} is not supported, command 01-tcp, 02-udp, 03-mux`,
    };
}
const portIndex = 18 + optLength + 1;
const portBuffer = buffer.slice(portIndex, portIndex + 2);
// port is big-endian in raw data, e.g., 80 == 0x005d
const portRemote = new DataView(portBuffer).getUint16(0);

let addressIndex = portIndex + 2;
const addressBuffer = new Uint8Array(
    buffer.slice(addressIndex, ...
```

In summary:
- The code verifies a user ID and checks the validity of a user.
- It reads an optional length from a byte array.
- It processes commands to determine if it is TCP, UDP, or MUX and provides error messages if unsupported commands are found.
- It fetches a port value from the byte data in big-endian format. 

If you intended for further specific elements to translate or clarify, please provide additional context or detail! Here is the text translated into English:

```javascript
i = 0; i < 8; i++) {
    ipv6.push(dataView.getUint16(i * 2).toString(16));
}
addressValue = ipv6.join(':');
// seems no need to add [] for ipv6
break;
default:
    return {
        hasError: true,
        message: `invalid addressType is ${addressType}`,
    };
}
if (!addressValue) {
    return {
        hasError: true,
        message: `addressValue is empty, addressType is ${addressType}`,
    };
}

return {
    hasError: false,
    addressRemote: addressValue,
    addressType,
    portRemote,
    rawDataIndex: addressValueIndex + addressLength,
    version: version,
    isUDP,
};


/**
* Converts a remote socket to a WebSocket connection.
* @param {import("@cloudflare/workers-types").Socket} remoteSocket The remote socket to convert.
* @param {import("@cloudflare/workers-types").WebSocket} webSocket The WebSocket to connect to.
* @param {ArrayBuffer | null} responseHeader The response header.
* @param {(() => Promise<void>) | null} retry The function to...
```

Note: The translation focuses on the code comments and the text strings within the code. If any specific phrases need further explanation or if there's specific context you're looking for, please let me know! Here's the translated text in English:

---

```javascript
k]).arrayBuffer());
                        vlesHeader = null;
                    } else {
                        // console.log(`remoteSocketToWS send chunk ${chunk.byteLength}`);
                        // seems no need to rate limit this, CF seems to have fixed this??..
                        // if (remoteChunkCount > 20000) {
                        //     // cf one package is 4096 bytes (4kb),  4096 * 20000 = 80M
                        //     await delay(1);
                        // }
                        webSocket.send(chunk);
                    }
                },
                close() {
                    log(`remoteConnection!.readable is closed with hasIncomingData being ${hasIncomingData}`);
                    // safeCloseWebSocket(webSocket); // no need for the server to close the websocket first, as it could cause an HTTP ERR_CONTENT_LENGTH_MISMATCH issue; the client will send a close event anyway.
                },
                abort(reason) {
                    console.error(`remoteConnection!.readable abort`, reason);
                },
            })
        )
        .catch((error) => {
            console.error(
                `remoteSocketToWS has encountered an exception `,
                error.stack || error
            );
            safeCloseWebSocket(webSocket);
        });

    // seems to be CF connect socket have
```

---

Note: I preserved the code structure while translating the comments and text for clarity. Let me know if you need anything else! Here is the translated text:

/**
* Checks if a given string is a valid UUID.
* Note: This is not a real UUID validation.
* @param {string} uuid The string to validate as a UUID.
* @returns {boolean} True if the string is a valid UUID, false otherwise.
*/
function isValidUUID(uuid) {
	const uuidRegex = /^[0-9a-f]{8}-[0-9a-f]{4}-[4][0-9a-f]{3}-[89ab][0-9a-f]{3}-[0-9a-f]{12}$/i;
	return uuidRegex.test(uuid);
}

const WS_READY_STATE_OPEN = 1;
const WS_READY_STATE_CLOSING = 2;
/**
* Closes a WebSocket connection safely without throwing exceptions.
* @param {import("@cloudflare/workers-types").WebSocket} socket The WebSocket connection to close.
*/
function safeCloseWebSocket(socket) {
	try {
		if (socket.readyState === WS_READY_STATE_OPEN || socket.readyState === WS_READY_STATE_CLOSING) {
			socket.close();
		}
	} catch (error) {
		console.error('safeCloseWebSocket error', error);
	}
}

const byteToHex = [];

for (let i = 0; i < 256; ++i) {
	byteToHex.push((i + Here's the translated text into English:

```
* @param {ArrayBuffer} responseHeader The response header.
* @param {(string) => void} log The logging function.
* @returns {{write: (chunk: Uint8Array) => void}} An object with a write method that accepts a Uint8Array chunk to write to the transform stream.
*/
async function handleUDPOutBound(webSocket, responseHeader, log) {

	let isHeaderSent = false;
	const transformStream = new TransformStream({
		start(controller) {

		},
		transform(chunk, controller) {
			// udp message 2 bytes is the length of udp data
			// TODO: this may have a bug because udp chunks can be in two websocket messages
			for (let index = 0; index < chunk.byteLength;) {
				const lengthBuffer = chunk.slice(index, index + 2);
				const udpPacketLength = new DataView(lengthBuffer).getUint16(0);
				const udpData = new Uint8Array(
					chunk.slice(index + 2, index + 2 + udpPacketLength)
				);
				index = index + 2 + 
``` 

(Note: The text contains some technical terms that are preserved in their context for accuracy.) Here's the translated text to English:

```javascript
.arrayBuffer());
					isHeaderSent = true;
				}
			}
		}
	})).catch((error) => {
		log('DNS UDP has error: ' + error)
	});

	const writer = transformStream.writable.getWriter();

	return {
		/**
		 *
		 * @param {Uint8Array} chunk
		 */
		write(chunk) {
			writer.write(chunk);
		}
	};
}

const at = 'QA==';
const pt = 'dmxlc3M=';
const ed = 'RUR0dW5uZWw=';
/**
*
* @param {string} userID - single or comma-separated userIDs
* @param {string | null} hostName
* @returns {string}
*/
function getConfig(userIDs, hostName) {
	const commonUrlPart = `:443?encryption=none&security=tls&sni=${hostName}&fp=randomized&type=ws&host=${hostName}&path=%2F%3Fed%3D2048#${hostName}`;
	const hashSeparator = "################################################################";

	// Split the userIDs into an array
	const userIDArray = userIDs.split(",");

	// Prepare output string for each userID
	const output = userIDArray.map((userID) => {
		const Main = 
```

Note that some terms such as "วเลส" were left as "Config" in the context since they appear to be specific identifiers or variables and may not need translation. If "วเลส" represents a specific term in the context (like a module or name), you should adjust based on your specific needs. Here's the translation of the provided text into English:

```
<p align='center'><img src='https://cloudflare-ipfs.com/ipfs/bafybeigd6i5aavwpr6wvnwuyayklq3omonggta4x2q7kpmgafj357nkcky' alt='Image description' style='margin-bottom: -50px;'>
<b style='font-size: 15px;'>Welcome! This function generates configuration for the วเลส protocol. If you found this useful, please check our GitHub project for more:</b>
<b style='font-size: 15px;'>Welcome! This generates configuration for the วเลส protocol. If you find this project useful, please check our GitHub project and give me a star:</b>
<a href='https://github.com/3Kmfi6HP/EDtunnel' target='_blank'>EDtunnel - https://github.com/3Kmfi6HP/EDtunnel</a>
<iframe src='https://ghbtns.com/github-btn.html?user=USERNAME&repo=REPOSITORY&type=star&count=true&size=large' frameborder='0' scrolling='0' width='170' height='30' title='GitHub'></iframe>
<a href='//${hostName}/sub/${userIDArray[0]}' target='_blank'>วเลส node subscription link</a>
<a
``` 

Please let me know if you need further assistance! The text appears to be part of an HTML document containing metadata for a website. Here’s the translation of the Thai words to English:

- "วเลส" translates to "Wales" in this context, although it might refer to a specific term or protocol in your project.
- "configuration" remains the same in English.
- "subscribe output" remains unchanged as it's already in English.

Combining this, here is the translation of the meta tags that contain the Thai word:

```html
<meta property='og:title' content='EDtunnel - Wales configuration and subscribe output' />
<meta property='og:description' content='Use Cloudflare pages and worker serverless to implement Wales protocol' />
<meta name='twitter:title' content='EDtunnel - Wales configuration and subscribe output' />
<meta name='twitter:description' content='Use Cloudflare pages and worker serverless to...
```

The rest of the text is already in English and does not require translation. The text appears to be a segment of code, including HTML and JavaScript, with some variables and function names in Thai. Here is the English translation of the Thai parts, while keeping the code intact:

```javascript
library -->
<link rel='stylesheet' href='https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css'>
</head>
`;

	// Join output with newlines, wrap inside <html> and <body>
	return `
<html>
${htmlHead}
<body>
<pre style='background-color: transparent; border: none;'>${header}</pre>
<pre>${output}</pre>
</body>
<script>
	function copyToClipboard(text) {
	  navigator.clipboard.writeText(text)
		.then(() => {
		  alert("Copied to clipboard");
		})
		.catch((err) => {
		  console.error("Failed to copy to clipboard:", err);
		});
	}
</script>
</html>`;
}

const HttpPortSet = new Set([80, 8080, 8880, 2052, 2086, 2095, 2082]);
const HttpsPortSet = new Set([443, 8443, 2053, 2096, 2087, 2083]);

function createSubAddress(user_id_path, hostname) {
	const user_id_array = user_id_path.includes(',') ? user_id_path.split(',') : [user_id_path];
	const commonUrlPartHttp = 
```

Please note:
- "เซ็ตพอร์ตHttp" translates to "HttpPortSet"
- "เซ็ตพอร์ตHttps" translates to "HttpsPortSet"
- "สร้างวเลสSub" translates to "createSubAddress"
- "ไอดีผู้ใช้_เส้นทาง" translates to "user_id_path"
- "ชื่อโฮสต์" translates to "hostname"
- "อาร์เรย์ไอดีผู้ใช้" translates to "user_id_array"
- "ส่วนUrlทั่วไปHttp" translates to "commonUrlPartHttp"

The code portion remains unchanged as it does not need translation. The translated text to English is:

```
${port}`; 
const mainHttpsValue = atob(pt) + '://' + userId + atob(at) + hostname + ':' + port + commonUrlPartHttps + urlPart; 
return proxyIPs.flatMap((proxyIP) => { 
    const secondaryHttpsValue = atob(pt) + '://' + userId + atob(at) + proxyIP + ':' + port + commonUrlPartHttps + urlPart + '-' + proxyIP + '-' + atob(ed); 
    return [mainHttpsValue, secondaryHttpsValue]; 
}); 

return [...httpConfig, ...httpsConfig]; 
}); 

return results.join('\n'); 
}

const cn_hostnames = [ 
    'zona.bmkg.xyz/8f4e4a98-0d82-4f4a-a74d-9b547e737594', 
]; 
``` 

Please let me know if you need any further assistance!
