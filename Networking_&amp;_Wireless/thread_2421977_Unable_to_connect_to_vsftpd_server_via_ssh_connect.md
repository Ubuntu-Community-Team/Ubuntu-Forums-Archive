---
title: "Unable to connect to vsftpd server via ssh connection"
date: 2019-06-30
forum: Networking &amp; Wireless
---

### Post by scporse on 2019-06-30
Greetings,

First, a bit of background:

I've set up an OpenSSH server on my local media center (htpc, running Ubuntu 16.04 LTS) and I then connect to that externally, via SSH, by using the VX Connectbot app on my Android device - using this guide: [https://thepcspy.com/read/remote-streaming-access-xbmc-kodi/](https://thepcspy.com/read/remote-streaming-access-xbmc-kodi/)
In VX Connectbot I've also configured local port forwards for the "htpc" ssh connection, enabling me to reach a kodi instance and a transmission daemon, through the ssh tunnel.
This is working quite well, and therefore I expected to be able to use the same technique for reaching the vsftpd server on the very same machine.

That, however, hasn't been the case, as I've been unable to connect the ftp server, in spite of having configured a local port forward for this exact purpose.

These are the port forwards currently configured for the htpc ssh connection in VX Connectbot:

Name: transmission http
Type: local
Source port: 9091
Destination: localhost:80

Name: kodi http
Type: local
Source port: 8080
Destination: localhost:8080

Name: ftp
Type: local
Source port: 21212
Destination: localhost:21

As already mentioned, the first two port forwards above work as expected, but the third one, for ftp, does not.

In the ftp client app (currently using Solid explorer, but have tried a few others), I have created a ftp connection with the following settings:

Name: htpc (remote)
Remote host name: localhost
Port number: 21212
(Path and username/password left out).

(Just to be clear, I do have another ftp connection configured in the same app for connecting to the ftp server while on the home network, and this works without issues.

When I try to connect to the ftp server externally, I get the error: Connection refused.

It  would be tempting to think that I'm simply dealing with a firewall  issue here, but I don't believe that to be the case, as I get these  lines in /var/log/vsftpd.log, when attempting an FTP connection from my Android device, which tells me that the ftp client actually does reach the  ftp server, while still being unable to actually establish a connection:

Sun Jun 30 00:23:41 2019 [pid 31298] CONNECT: Client "::ffff:127.0.0.1"
Sun Jun 30 00:23:41 2019 [pid 31297] [soren] OK LOGIN: Client "::ffff:127.0.0.1"
Sun Jun 30 00:23:42 2019 [pid 31306] CONNECT: Client "::ffff:127.0.0.1"
Sun Jun 30 00:23:42 2019 [pid 31304] [soren] OK LOGIN: Client "::ffff:127.0.0.1"


I really hope someone has an idea about what I might have done wrong here  as I'm pretty much out of ideas, having tested every aspect of the  configuration I could think of.

---

### Post by scporse on 2019-06-30
Could it be something to do with the data connection port for ftp (port 20) not being forwarded? I tried to do this, but VX Connectbot seems to not allow port forwards below 1024.

---

### Post by scporse on 2019-06-30
I couldn't get FTP to work, so switched to SCP instead (using the AndFTP Android app).

---

