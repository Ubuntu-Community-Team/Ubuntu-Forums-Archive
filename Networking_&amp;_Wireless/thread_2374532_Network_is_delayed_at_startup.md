---
title: "Network is delayed at startup"
date: 2017-10-16
forum: Networking &amp; Wireless
---

### Post by matthias-karl on 2017-10-16
Hi

I had an ubuntu server running Plex Media Server for some time and it worked just fine. When I recently tried to update the server to a new version, it somehow crashed and I had to do a clean re-install. That went fairly smooth and it is up and running again.

Although now I have a small problem that comes up after each reboot. Plex server apparently can't log in as the network service is not yet fully up and running. So I always have to do that manually. Below are some of the errors from the Plex log file.

```
Oct 16, 2017 23:27:45.183 [0x7f4932ffd700] DEBUG - HTTP requesting GET http://ocspx.digicert.com/MFEwTzBNMEswSTAJBgUrDgMCGgUABBSnVdbEyh8T3xvVlkPGHNCJxnqCPgQUlIuJ90hyifJRStmIe%2BVhtaqc1QECEAMVVDbxqYUVmXkjHTV9sBY%3D
Oct 16, 2017 23:27:45.186 [0x7f4932ffd700] ERROR - Error issuing curl_easy_perform(handle): 6
Oct 16, 2017 23:27:45.186 [0x7f4932ffd700] WARN - HTTP error requesting GET http://ocspx.digicert.com/MFEwTzBNMEswSTAJBgUrDgMCGgUABBSnVdbEyh8T3xvVlkPGHNCJxnqCPgQUlIuJ90hyifJRStmIe%2BVhtaqc1QECEAMVVDbxqYUVmXkjHTV9sBY%3D (0, No error) (Couldn't resolve host 'ocspx.digicert.com')
Oct 16, 2017 23:27:45.186 [0x7f4932ffd700] ERROR - OCSP response error: -6  Oct 16, 2017 23:27:45.234 [0x7f492dffe700] DEBUG - HTTP requesting GET https://plex.tv/servers/baa4d0baa6fa4a7827eacab9bf56a7a0c374c1c2/access_tokens.xml?auth_token=xxxxxxxxxxxxxxxxxxxx&includeProfiles=1&includeProviders=1
Oct 16, 2017 23:27:45.235 [0x7f492dffe700] ERROR - Error issuing curl_easy_perform(handle): 6
Oct 16, 2017 23:27:45.235 [0x7f492dffe700] WARN - HTTP error requesting GET https://plex.tv/servers/baa4d0baa6fa4a7827eacab9bf56a7a0c374c1c2/access_tokens.xml?auth_token=xxxxxxxxxxxxxxxxxxxx&includeProfiles=1&includeProviders=1 (0, No error) (Couldn't resolve host 'plex.tv')
```

This shows the LAN interface was not visible

  ```
Oct 16, 2017 23:27:47.198 [0x7f4942ad8800] DEBUG - Network interfaces:
Oct 16, 2017 23:27:47.198 [0x7f4942ad8800] DEBUG -  * 1 lo (127.0.0.1) (loopback: 1)
```

and more DNS lookup errors

  ```
Oct 16, 2017 23:27:47.198 [0x7f492dffe700] WARN - HTTP error requesting PUT https://plex.tv/devices/baa4d0baa6fa4a7827eacab9bf56a7a0c374c1c2?httpsEnabled=1&httpsRequired=0&X-Plex-Token=xxxxxxxxxxxxxxxxxxxx (0, No error) (Couldn't resolve host 'plex.tv')  Oct 16, 2017 23:27:47.199 [0x7f4934fff700] ERROR - Error issuing curl_easy_perform(handle): 6
Oct 16, 2017 23:27:47.199 [0x7f4934fff700] WARN - HTTP error requesting PUT https://plex.tv/devices/baa4d0baa6fa4a7827eacab9bf56a7a0c374c1c2?httpsEnabled=1&httpsRequired=0&X-Plex-Token=xxxxxxxxxxxxxxxxxxxx (0, No error) (Couldn't resolve host 'plex.tv')  Oct 16, 2017 23:27:47.261 [0x7f492c3fe700] WARN - HTTP error requesting PUT https://plex.tv/devices/baa4d0baa6fa4a7827eacab9bf56a7a0c374c1c2?httpsEnabled=1&httpsRequired=0&X-Plex-Token=xxxxxxxxxxxxxxxxxxxx (0, No error) (Couldn't resolve host 'plex.tv')  Oct 16, 2017 23:27:47.263 [0x7f492cbff700] WARN - HTTP error requesting PUT https://plex.tv/devices/baa4d0baa6fa4a7827eacab9bf56a7a0c374c1c2?httpsEnabled=1&httpsRequired=0&X-Plex-Token=xxxxxxxxxxxxxxxxxxxx (0, No  error) (Couldn't resolve host 'plex.tv') 
```
It was only at this point that the LAN interface became visible

  ```
Oct 16, 2017 23:27:47.301 [0x7f49273ff700] DEBUG - NetworkInterface: Notified of network changed (force=0)
Oct 16, 2017 23:27:47.302 [0x7f49273ff700] DEBUG - Network interfaces:
Oct 16, 2017 23:27:47.302 [0x7f49273ff700] DEBUG -  * 1 lo (127.0.0.1) (loopback: 1)
Oct 16, 2017 23:27:47.302 [0x7f49273ff700] DEBUG -  * 2 enp3s0 (192.168.0.6) (loopback: 0)
```

DNS lookups continued to fail

  ```
Oct 16, 2017 23:27:47.304 [0x7f492e7ff700] ERROR - Error issuing curl_easy_perform(handle): 6
Oct 16, 2017 23:27:47.304 [0x7f492e7ff700] WARN - HTTP error requesting PUT https://plex.tv/devices/baa4d0baa6fa4a7827eacab9bf56a7a0c374c1c2?Connection[][uri]=http://192.168.0.6:32400&httpsEnabled=1&httpsRequired=0&X-Plex-Token=xxxxxxxxxxxxxxxxxxxx (0, No error) (Couldn't resolve host 'plex.tv')
```

Then at this time - it started to work

  ```
Oct 16, 2017 23:27:50.469 [0x7f491fbff700] DEBUG - HTTP 200 response from GET https://plex.tv/updater/products/1/check.xml?build=linux-ubuntu-x86_64&channel=16&distribution=ubuntu&version=1.9.4.4325-1bf240a65
```

Is there a way to ensure that the network is up and running as it should before it proceeds with booting up?

Or as an alternative, can I somehow delay the startup of Plex to wait till the network is fully up?

I have the following installed:

```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:        16.04
Codename:    xenial

Linux nostromo 4.10.0-37-generic #41~16.04.1-Ubuntu SMP Fri Oct 6 22:42:59 UTC 2017 x86_64 x86_64x86_64 GNU/Linux

```

The machine is connected with a cable to the router which provides a static IP address (192.168.0.6). 

As I am very inexperienced with Linux, please provide very detailed descriptions as to what I can do to get this working.

Thank you very much in advance.

---

### Post by matthias-karl on 2017-10-16
Here is the connection information for reference.

[IMG]https://image.ibb.co/jNMOD6/Network_Settings.png[/IMG]

---

