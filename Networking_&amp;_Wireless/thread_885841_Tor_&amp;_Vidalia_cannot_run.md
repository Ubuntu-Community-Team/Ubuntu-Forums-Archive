---
title: "Tor &amp; Vidalia cannot run?"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by eHobayyeb on 2008-08-10
I installed them and FoxyProxy but I cannot connect using Tor??

See this log message from Vidalia:
```

Aug 10 21:52:17.979 [Notice] Tor v0.1.2.19. This is experimental software. Do not rely on it for strong anonymity.
Aug 10 21:52:17.980 [Notice] Initialized libevent version 1.3e using method epoll. Good.
Aug 10 21:52:17.980 [Notice] Opening Socks listener on 127.0.0.1:9050
Aug 10 21:52:17.980 [Notice] Opening Control listener on 127.0.0.1:9051
Aug 10 21:52:18.202 [Debug] conn_read_callback(): socket 9 wants to read.
Aug 10 21:52:29.224 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:52:40.264 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:52:51.304 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:53:02.348 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:53:13.388 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:53:24.428 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:53:35.472 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:53:46.516 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:53:57.560 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:54:08.592 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:54:19.631 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:54:30.676 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:54:41.716 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:54:52.760 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:55:03.799 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:55:14.828 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:55:25.860 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:55:27.180 [Debug] conn_read_callback(): socket 8 wants to read.
Aug 10 21:55:27.182 [Info] connection_close_immediate(): fd 8, type Directory, state connecting, 262 bytes on outbuf.
Aug 10 21:55:27.184 [Debug] conn_close_if_marked(): Cleaning up connection (fd -1).
Aug 10 21:55:27.186 [Info] connection_dir_request_failed(): Giving up on directory server at '128.31.0.34'; retrying
Aug 10 21:55:27.188 [Debug] connection_remove(): removing socket -1 (type Directory), n_conns now 3
Aug 10 21:55:27.868 [Info] update_router_have_minimum_dir_info(): We have 0 of 5 network statuses, and we want more than 2.
Aug 10 21:55:36.904 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:55:47.948 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:55:58.992 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:56:09.028 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:56:20.064 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:56:22.069 [Info] update_networkstatus_client_downloads(): For 5/5 running directory servers, we have 0 live network-status documents. Downloading 5.
Aug 10 21:56:22.072 [Info] router_pick_directory_server(): No reachable router entries for dirservers. Trying them all again.
Aug 10 21:56:22.075 [Info] router_pick_directory_server(): Still no reachable router entries. Reloading and trying again.
Aug 10 21:56:22.077 [Info] tor_mmap_file(): Could not open "/home/ehobayyeb/.tor/cached-routers" for mmap(): No such file or directory
Aug 10 21:56:22.080 [Info] directory_get_from_dirserver(): No router found for network status; falling back to dirserver list
Aug 10 21:56:22.083 [Debug] directory_initiate_command(): private 0, want_to_tunnel 0.
Aug 10 21:56:22.084 [Debug] directory_initiate_command(): initiating network-status fetch
Aug 10 21:56:22.085 [Debug] connection_connect(): Connecting to [scrubbed]:9031.
Aug 10 21:56:22.087 [Debug] connection_connect(): Connection to [scrubbed]:9031 in progress (sock 8).
Aug 10 21:56:22.088 [Debug] connection_add(): new conn type Directory, socket 8, n_conns 4.
Aug 10 21:56:22.089 [Debug] write_to_buf(): added 4 bytes to buf (now 4 total).
Aug 10 21:56:22.090 [Debug] write_to_buf(): added 221 bytes to buf (now 225 total).
Aug 10 21:56:22.091 [Debug] write_to_buf(): added 37 bytes to buf (now 262 total).
Aug 10 21:56:22.093 [Info] update_router_have_minimum_dir_info(): We have 0 of 5 network statuses, and we want more than 2.
Aug 10 21:56:31.104 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:56:42.140 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:56:53.180 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:57:04.224 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:57:15.260 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:57:26.296 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:57:37.340 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:57:48.379 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:57:59.416 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:58:10.453 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:58:21.497 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:58:32.540 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:58:43.584 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:58:54.631 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:59:05.660 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:59:16.704 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:59:27.748 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:59:31.068 [Debug] conn_read_callback(): socket 8 wants to read.
Aug 10 21:59:31.070 [Info] connection_close_immediate(): fd 8, type Directory, state connecting, 262 bytes on outbuf.
Aug 10 21:59:31.072 [Debug] conn_close_if_marked(): Cleaning up connection (fd -1).
Aug 10 21:59:31.073 [Info] connection_dir_request_failed(): Giving up on directory server at '128.31.0.34'; retrying
Aug 10 21:59:31.075 [Debug] connection_remove(): removing socket -1 (type Directory), n_conns now 3
Aug 10 21:59:31.763 [Info] update_router_have_minimum_dir_info(): We have 0 of 5 network statuses, and we want more than 2.
Aug 10 21:59:38.788 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 21:59:49.828 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:00:00.868 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:00:11.916 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:00:22.957 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:00:26.972 [Info] update_networkstatus_client_downloads(): For 5/5 running directory servers, we have 0 live network-status documents. Downloading 5.
Aug 10 22:00:26.975 [Info] router_pick_directory_server(): No reachable router entries for dirservers. Trying them all again.
Aug 10 22:00:26.977 [Info] router_pick_directory_server(): Still no reachable router entries. Reloading and trying again.
Aug 10 22:00:26.979 [Info] tor_mmap_file(): Could not open "/home/ehobayyeb/.tor/cached-routers" for mmap(): No such file or directory
Aug 10 22:00:26.981 [Info] directory_get_from_dirserver(): No router found for network status; falling back to dirserver list
Aug 10 22:00:26.983 [Debug] directory_initiate_command(): private 0, want_to_tunnel 0.
Aug 10 22:00:26.986 [Debug] directory_initiate_command(): initiating network-status fetch
Aug 10 22:00:26.988 [Debug] connection_connect(): Connecting to [scrubbed]:9032.
Aug 10 22:00:26.990 [Debug] connection_connect(): Connection to [scrubbed]:9032 in progress (sock 8).
Aug 10 22:00:26.993 [Debug] connection_add(): new conn type Directory, socket 8, n_conns 4.
Aug 10 22:00:26.995 [Debug] write_to_buf(): added 4 bytes to buf (now 4 total).
Aug 10 22:00:27.004 [Debug] write_to_buf(): added 221 bytes to buf (now 225 total).
Aug 10 22:00:27.006 [Debug] write_to_buf(): added 37 bytes to buf (now 262 total).
Aug 10 22:00:27.009 [Info] update_router_have_minimum_dir_info(): We have 0 of 5 network statuses, and we want more than 2.
Aug 10 22:00:34.000 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:00:44.040 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:00:55.076 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:01:06.120 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:01:17.164 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:01:28.207 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:01:39.248 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:01:50.275 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:02:01.311 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:02:12.351 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:02:23.379 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:02:34.424 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:02:45.460 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:02:56.492 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:03:07.532 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:03:18.568 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:03:29.604 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:03:35.972 [Debug] conn_read_callback(): socket 8 wants to read.
Aug 10 22:03:35.975 [Info] connection_close_immediate(): fd 8, type Directory, state connecting, 262 bytes on outbuf.
Aug 10 22:03:35.978 [Debug] conn_close_if_marked(): Cleaning up connection (fd -1).
Aug 10 22:03:35.986 [Info] connection_dir_request_failed(): Giving up on directory server at '128.31.0.34'; retrying
Aug 10 22:03:35.989 [Debug] connection_remove(): removing socket -1 (type Directory), n_conns now 3
Aug 10 22:03:36.632 [Info] update_router_have_minimum_dir_info(): We have 0 of 5 network statuses, and we want more than 2.
Aug 10 22:03:40.656 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:03:51.685 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:04:02.724 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:04:13.767 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:04:24.812 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:04:30.840 [Info] update_networkstatus_client_downloads(): For 5/5 running directory servers, we have 0 live network-status documents. Downloading 5.
Aug 10 22:04:30.845 [Info] router_pick_directory_server(): No reachable router entries for dirservers. Trying them all again.
Aug 10 22:04:30.850 [Info] router_pick_directory_server(): Still no reachable router entries. Reloading and trying again.
Aug 10 22:04:30.854 [Info] tor_mmap_file(): Could not open "/home/ehobayyeb/.tor/cached-routers" for mmap(): No such file or directory
Aug 10 22:04:30.859 [Info] directory_get_from_dirserver(): No router found for network status; falling back to dirserver list
Aug 10 22:04:30.863 [Debug] directory_initiate_command(): private 0, want_to_tunnel 0.
Aug 10 22:04:30.867 [Debug] directory_initiate_command(): initiating network-status fetch
Aug 10 22:04:30.876 [Debug] connection_connect(): Connecting to [scrubbed]:80.
Aug 10 22:04:30.881 [Debug] connection_connect(): Connection to [scrubbed]:80 in progress (sock 8).
Aug 10 22:04:30.898 [Debug] connection_add(): new conn type Directory, socket 8, n_conns 4.
Aug 10 22:04:30.901 [Debug] write_to_buf(): added 4 bytes to buf (now 4 total).
Aug 10 22:04:30.909 [Debug] write_to_buf(): added 221 bytes to buf (now 225 total).
Aug 10 22:04:30.913 [Debug] write_to_buf(): added 36 bytes to buf (now 261 total).
Aug 10 22:04:30.916 [Info] update_router_have_minimum_dir_info(): We have 0 of 5 network statuses, and we want more than 2.
Aug 10 22:04:31.384 [Debug] conn_write_callback(): socket 8 wants to write.
Aug 10 22:04:31.388 [Debug] connection_dir_finished_connecting(): Dir connection to router 194.109.206.212:80 established.
Aug 10 22:04:31.391 [Debug] flush_buf(): 8: flushed 261 bytes, 0 ready to flush, 0 remain.
Aug 10 22:04:31.395 [Debug] connection_dir_finished_flushing(): client finished sending command.
Aug 10 22:04:31.843 [Debug] global_write_bucket now 6291456.
Aug 10 22:04:35.860 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:04:46.904 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:04:57.943 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:05:08.987 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:05:19.020 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:05:30.060 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:05:31.113 [Debug] conn_read_callback(): socket 8 wants to read.
Aug 10 22:05:31.117 [Debug] read_to_buf_impl(): Encountered eof
Aug 10 22:05:31.121 [Debug] fetch_from_buf_http(): headers not all here yet.
Aug 10 22:05:31.125 [Info] connection_dir_client_reached_eof(): 'fetch' response not all here, but we're at eof. Closing.
Aug 10 22:05:31.129 [Debug] conn_close_if_marked(): Cleaning up connection (fd 8).
Aug 10 22:05:31.133 [Info] connection_dir_request_failed(): Giving up on directory server at '194.109.206.212'; retrying
Aug 10 22:05:31.137 [Debug] connection_remove(): removing socket 8 (type Directory), n_conns now 3
Aug 10 22:05:31.153 [Debug] _connection_free(): closing fd 8.
Aug 10 22:05:32.068 [Info] update_router_have_minimum_dir_info(): We have 0 of 5 network statuses, and we want more than 2.
Aug 10 22:05:41.104 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:05:52.139 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:06:03.176 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:06:14.211 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:06:25.243 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:06:32.272 [Info] update_networkstatus_client_downloads(): For 5/5 running directory servers, we have 0 live network-status documents. Downloading 5.
Aug 10 22:06:32.276 [Info] router_pick_directory_server(): No reachable router entries for dirservers. Trying them all again.
Aug 10 22:06:32.281 [Info] router_pick_directory_server(): Still no reachable router entries. Reloading and trying again.
Aug 10 22:06:32.285 [Info] tor_mmap_file(): Could not open "/home/ehobayyeb/.tor/cached-routers" for mmap(): No such file or directory
Aug 10 22:06:32.289 [Info] directory_get_from_dirserver(): No router found for network status; falling back to dirserver list
Aug 10 22:06:32.293 [Debug] directory_initiate_command(): private 0, want_to_tunnel 0.
Aug 10 22:06:32.310 [Debug] directory_initiate_command(): initiating network-status fetch
Aug 10 22:06:32.317 [Debug] connection_connect(): Connecting to [scrubbed]:80.
Aug 10 22:06:32.321 [Debug] connection_connect(): Connection to [scrubbed]:80 in progress (sock 8).
Aug 10 22:06:32.326 [Debug] connection_add(): new conn type Directory, socket 8, n_conns 4.
Aug 10 22:06:32.331 [Debug] write_to_buf(): added 4 bytes to buf (now 4 total).
Aug 10 22:06:32.338 [Debug] write_to_buf(): added 221 bytes to buf (now 225 total).
Aug 10 22:06:32.348 [Debug] write_to_buf(): added 34 bytes to buf (now 259 total).
Aug 10 22:06:32.352 [Info] update_router_have_minimum_dir_info(): We have 0 of 5 network statuses, and we want more than 2.
Aug 10 22:06:32.886 [Debug] conn_write_callback(): socket 8 wants to write.
Aug 10 22:06:32.890 [Debug] connection_dir_finished_connecting(): Dir connection to router 140.247.60.64:80 established.
Aug 10 22:06:32.898 [Debug] flush_buf(): 8: flushed 259 bytes, 0 ready to flush, 0 remain.
Aug 10 22:06:32.903 [Debug] connection_dir_finished_flushing(): client finished sending command.
Aug 10 22:06:33.272 [Debug] global_write_bucket now 6291456.
Aug 10 22:06:36.283 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:06:47.321 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:06:58.360 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:07:09.399 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:07:20.440 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:07:31.485 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:07:36.354 [Debug] conn_read_callback(): socket 8 wants to read.
Aug 10 22:07:36.359 [Debug] read_to_buf_impl(): Encountered eof
Aug 10 22:07:36.364 [Debug] fetch_from_buf_http(): headers not all here yet.
Aug 10 22:07:36.370 [Info] connection_dir_client_reached_eof(): 'fetch' response not all here, but we're at eof. Closing.
Aug 10 22:07:36.375 [Debug] conn_close_if_marked(): Cleaning up connection (fd 8).
Aug 10 22:07:36.383 [Info] connection_dir_request_failed(): Giving up on directory server at '140.247.60.64'; retrying
Aug 10 22:07:36.388 [Debug] connection_remove(): removing socket 8 (type Directory), n_conns now 3
Aug 10 22:07:36.393 [Debug] _connection_free(): closing fd 8.
Aug 10 22:07:36.503 [Info] update_router_have_minimum_dir_info(): We have 0 of 5 network statuses, and we want more than 2.
Aug 10 22:07:42.528 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:07:53.572 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:08:04.616 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:08:15.660 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:08:26.700 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:08:34.733 [Info] update_networkstatus_client_downloads(): For 5/5 running directory servers, we have 0 live network-status documents. Downloading 5.
Aug 10 22:08:34.747 [Info] router_pick_directory_server(): No reachable router entries for dirservers. Trying them all again.
Aug 10 22:08:34.760 [Info] router_pick_directory_server(): Still no reachable router entries. Reloading and trying again.
Aug 10 22:08:34.773 [Info] tor_mmap_file(): Could not open "/home/ehobayyeb/.tor/cached-routers" for mmap(): No such file or directory
Aug 10 22:08:34.787 [Info] directory_get_from_dirserver(): No router found for network status; falling back to dirserver list
Aug 10 22:08:34.800 [Debug] directory_initiate_command(): private 0, want_to_tunnel 0.
Aug 10 22:08:34.807 [Debug] directory_initiate_command(): initiating network-status fetch
Aug 10 22:08:34.812 [Debug] connection_connect(): Connecting to [scrubbed]:80.
Aug 10 22:08:34.818 [Debug] connection_connect(): Connection to [scrubbed]:80 in progress (sock 8).
Aug 10 22:08:34.823 [Debug] connection_add(): new conn type Directory, socket 8, n_conns 4.
Aug 10 22:08:34.831 [Debug] write_to_buf(): added 4 bytes to buf (now 4 total).
Aug 10 22:08:34.836 [Debug] write_to_buf(): added 221 bytes to buf (now 225 total).
Aug 10 22:08:34.841 [Debug] write_to_buf(): added 36 bytes to buf (now 261 total).
Aug 10 22:08:34.847 [Info] update_router_have_minimum_dir_info(): We have 0 of 5 network statuses, and we want more than 2.
Aug 10 22:08:35.047 [Debug] conn_write_callback(): socket 8 wants to write.
Aug 10 22:08:35.061 [Debug] connection_dir_finished_connecting(): Dir connection to router 194.109.206.212:80 established.
Aug 10 22:08:35.075 [Debug] flush_buf(): 8: flushed 261 bytes, 0 ready to flush, 0 remain.
Aug 10 22:08:35.090 [Debug] connection_dir_finished_flushing(): client finished sending command.
Aug 10 22:08:35.736 [Debug] global_write_bucket now 6291456.
Aug 10 22:08:37.743 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:08:48.784 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:08:59.828 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:09:10.867 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:09:21.900 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.
Aug 10 22:09:32.940 [Info] update_router_descriptor_client_downloads(): Not enough networkstatus documents to launch requests.

```

And this from Tor it self via Terminal:
```

ehobayyeb@ehobayyeb-laptop:~$ tor
Aug 10 21:47:51.516 [notice] Tor v0.1.2.19. This is experimental software. Do not rely on it for strong anonymity.
Aug 10 21:47:51.518 [notice] Initialized libevent version 1.3e using method epoll. Good.
Aug 10 21:47:51.518 [notice] Opening Socks listener on 127.0.0.1:9050
Aug 10 21:47:51.910 [notice] I learned some more directory information, but not enough to build a circuit.
Aug 10 21:48:35.972 [notice] Catching signal TERM, exiting cleanly.
ehobayyeb@ehobayyeb-laptop:~$ 

```

Please help me!

---

