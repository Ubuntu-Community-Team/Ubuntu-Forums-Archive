---
title: "SSH With Obfsproxy: Corrupted magic value"
date: 2015-11-28
forum: Networking &amp; Wireless
---

### Post by war59312 on 2015-11-28
Hi,

I am trying to get SSH working with Obfsproxy. Could use some help please.

Started Obfsproxy with:

```
sudo obfsproxy --log-file=/home/UserName/obfsproxy/obfsproxy.log --log-min-severity=debug obfs2 --dest=127.0.0.1:22 server 0.0.0.0:85
```

Obfsproxy Log:

```
2015-11-28 22:41:54,569 [WARNING] Obfsproxy (version: 0.2.13) starting up.
2015-11-28 22:41:54,569 [DEBUG] argv: ['/usr/local/bin/obfsproxy', '--log-file=/home/UserName/obfsproxy/obfsproxy.log', '--log-min-severity=debug', 'obfs2', '--dest=127.0.0.1:22', 'server', '0.0.0.0:85']
2015-11-28 22:41:54,569 [DEBUG] args: Namespace(data_dir=None, dest=('127.0.0.1', 22), ext_cookie_file=None, listen_addr=('0.0.0.0', 85), log_file='/home/UserName/obfsproxy/obfsproxy.log', log_min_severity='debug', mode='server', name='obfs2', no_log=False, no_safe_logging=False, proxy=None, shared_secret=None, ss_hash_iterations=None, validation_function=<bound method type.validate_external_mode_cli of <class 'obfsproxy.transports.obfs2.Obfs2Transport'>>)
2015-11-28 22:41:54,570 [INFO] StaticDestinationServerFactory starting on 85
2015-11-28 22:41:54,570 [INFO] Starting factory <obfsproxy.network.network.StaticDestinationServerFactory instance at 0x7f3ff3273200>
2015-11-28 22:41:54,570 [DEBUG] fact_s_0x7f3ff3273200: Starting up static destination server factory.
2015-11-28 22:41:54,570 [INFO] Launched 'server' listener at '[scrubbed]:85' for transport 'obfs2'.
2015-11-28 22:42:03,036 [DEBUG] fact_s_0x7f3ff3273200: New connection from [scrubbed]:61871.
2015-11-28 22:42:03,037 [INFO] Starting factory <obfsproxy.network.network.StaticDestinationClientFactory instance at 0x7f3ff3273c20>
2015-11-28 22:42:03,037 [DEBUG] fact_c_0x7f3ff3273c20: Client factory started connecting.
2015-11-28 22:42:03,037 [DEBUG] conn_0x7f3ff3276690: connectionMade (server): Setting it as downstream on our circuit.
2015-11-28 22:42:03,037 [DEBUG] circ_0x7f3ff3273bd8: Setting downstream connection (conn_0x7f3ff3276690).
2015-11-28 22:42:03,038 [DEBUG] conn_0x7f3ff3276690: Incomplete circuit; cached 67 bytes.
2015-11-28 22:42:03,038 [DEBUG] conn_0x7f3ff3276a10: connectionMade (server): Setting it as upstream on our circuit.
2015-11-28 22:42:03,038 [DEBUG] circ_0x7f3ff3273bd8: Setting upstream connection (conn_0x7f3ff3276a10).
2015-11-28 22:42:03,038 [DEBUG] circ_0x7f3ff3273bd8: Circuit completed.
2015-11-28 22:42:03,039 [DEBUG] obfs2 handshake: responder queued 2004 bytes (padding_length: 1980).
2015-11-28 22:42:03,039 [DEBUG] conn_0x7f3ff3276690: Writing 2004 bytes.
2015-11-28 22:42:03,047 [DEBUG] circ_0x7f3ff3273bd8: upstream: Received 43 bytes.
2015-11-28 22:42:03,047 [DEBUG] Got upstream data before doing handshake. Caching.
2015-11-28 22:42:03,049 [DEBUG] circ_0x7f3ff3273bd8: downstream: Received 67 bytes.
2015-11-28 22:42:03,049 [DEBUG] obfs2 receivedDownstream: Waiting for key.
2015-11-28 22:42:03,049 [DEBUG] obfs2 receivedDownstream: Got 43 bytes of handshake data (padding_length: 3131209175, magic: 0x56e9983f)
2015-11-28 22:42:03,049 [INFO] circ_0x7f3ff3273bd8: obfs2: Corrupted magic value '0x56e9983f': Closing circuit.
2015-11-28 22:42:03,049 [DEBUG] circ_0x7f3ff3273bd8: Tearing down circuit.
2015-11-28 22:42:03,050 [DEBUG] conn_0x7f3ff3276690: Closing connection.
2015-11-28 22:42:03,050 [DEBUG] conn_0x7f3ff3276a10: Closing connection.
2015-11-28 22:42:03,050 [DEBUG] conn_0x7f3ff3276690: Connection was lost (Connection was closed cleanly.).
2015-11-28 22:42:03,050 [DEBUG] conn_0x7f3ff3276a10: Connection was lost (Connection was closed cleanly.).
2015-11-28 22:42:03,050 [INFO] Stopping factory <obfsproxy.network.network.StaticDestinationClientFactory instance at 0x7f3ff3273c20>
```

Trying to connect to server from Win8.1 using Bitvise SSH Client @ [https://www.bitvise.com/ssh-client](https://www.bitvise.com/ssh-client)

And with Putty:

```
2015-11-28 22:35:04,612 [WARNING] Obfsproxy (version: 0.2.13) starting up.
2015-11-28 22:35:04,612 [DEBUG] argv: ['/usr/local/bin/obfsproxy', '--log-file=/home/UserName/obfsproxy/obfsproxy.log', '--log-min-severity=debug', 'obfs2', '--dest=127.0.0.1:22', 'server', '0.0.0.0:85']
2015-11-28 22:35:04,612 [DEBUG] args: Namespace(data_dir=None, dest=('127.0.0.1', 22), ext_cookie_file=None, listen_addr=('0.0.0.0', 85), log_file='/home/UserName/obfsproxy/obfsproxy.log', log_min_severity='debug', mode='server', name='obfs2', no_log=False, no_safe_logging=False, proxy=None, shared_secret=None, ss_hash_iterations=None, validation_function=<bound method type.validate_external_mode_cli of <class 'obfsproxy.transports.obfs2.Obfs2Transport'>>)
2015-11-28 22:35:04,613 [INFO] StaticDestinationServerFactory starting on 85
2015-11-28 22:35:04,613 [INFO] Starting factory <obfsproxy.network.network.StaticDestinationServerFactory instance at 0x7fe6c259c200>
2015-11-28 22:35:04,613 [DEBUG] fact_s_0x7fe6c259c200: Starting up static destination server factory.
2015-11-28 22:35:04,614 [INFO] Launched 'server' listener at '[scrubbed]:85' for transport 'obfs2'.
2015-11-28 22:35:23,234 [DEBUG] fact_s_0x7fe6c259c200: New connection from [scrubbed]:61324.
2015-11-28 22:35:23,234 [INFO] Starting factory <obfsproxy.network.network.StaticDestinationClientFactory instance at 0x7fe6c259cc20>
2015-11-28 22:35:23,234 [DEBUG] fact_c_0x7fe6c259cc20: Client factory started connecting.
2015-11-28 22:35:23,235 [DEBUG] conn_0x7fe6c259f690: connectionMade (server): Setting it as downstream on our circuit.
2015-11-28 22:35:23,235 [DEBUG] circ_0x7fe6c259cbd8: Setting downstream connection (conn_0x7fe6c259f690).
2015-11-28 22:35:23,236 [DEBUG] conn_0x7fe6c259f3d0: connectionMade (server): Setting it as upstream on our circuit.
2015-11-28 22:35:23,236 [DEBUG] circ_0x7fe6c259cbd8: Setting upstream connection (conn_0x7fe6c259f3d0).
2015-11-28 22:35:23,236 [DEBUG] circ_0x7fe6c259cbd8: Circuit completed.
2015-11-28 22:35:23,237 [DEBUG] obfs2 handshake: responder queued 4426 bytes (padding_length: 4402).
2015-11-28 22:35:23,237 [DEBUG] conn_0x7fe6c259f690: Writing 4426 bytes.
2015-11-28 22:35:23,243 [DEBUG] circ_0x7fe6c259cbd8: upstream: Received 43 bytes.
2015-11-28 22:35:23,243 [DEBUG] Got upstream data before doing handshake. Caching.
2015-11-28 22:35:23,247 [DEBUG] conn_0x7fe6c259f690: dataReceived called without a reason.
2015-11-28 22:35:53,245 [DEBUG] conn_0x7fe6c259f3d0: Connection was lost (Connection was closed cleanly.).
2015-11-28 22:35:53,246 [DEBUG] conn_0x7fe6c259f3d0: Closing connection.
2015-11-28 22:35:53,246 [DEBUG] circ_0x7fe6c259cbd8: Tearing down circuit.
2015-11-28 22:35:53,246 [DEBUG] conn_0x7fe6c259f690: Closing connection.
2015-11-28 22:35:53,246 [INFO] Stopping factory <obfsproxy.network.network.StaticDestinationClientFactory instance at 0x7fe6c259cc20>
2015-11-28 22:35:53,247 [DEBUG] conn_0x7fe6c259f690: Connection was lost (Connection was closed cleanly.).
```

Thank you,

Will

Update:

Turns out, this is NOT what I wanted anyways. But still, would have been nice if it worked as expected.

What I really need is @ [https://zinglau.github.io/projects/ObfuscatedOpenSSHPatches.html](https://zinglau.github.io/projects/ObfuscatedOpenSSHPatches.html) . Works great! :D

---

