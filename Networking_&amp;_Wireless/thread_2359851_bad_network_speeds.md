---
title: "bad network speeds?"
date: 2017-04-28
forum: Networking &amp; Wireless
---

### Post by ncage on 2017-04-28
Hello everyone. I&#8217;ve been fighting network speed issues since 14.04. I&#8217;ve upgraded to interim releases too (don&#8217;t just run LTS releases). I&#8217;ve been messing with smb.config. All distributions I run are ubuntu based. 2 Ubuntu & 1 Ubuntu Mate. My file server is Windows Server 2016 & was having this issue with Windows Server 2012 & 2012 R2. I&#8217;ve standardize on Intel gigabit Nics & have Cat 7 everywhere. I have 24 port trendnet switches that support Jumbo Frames up to 9K. 


Up to a week ago (so for a LONG time) I would get 10-12MBs/sec. Yes it was that bad. I was about to give up and go back to windows (or maybe try another non-ubuntu distro) until on my final search a week ago I found a obscure post (most are about smb.conf) that helped greatly located here:
[https://askubuntu.com/questions/764387/very-slow-internet-connection-on-ubuntu-16-04](https://askubuntu.com/questions/764387/very-slow-internet-connection-on-ubuntu-16-04)


this is the first time I have even heard gai.conf and the only post really about it. It made a huge difference. Now my upload speeds are ~60MB/s &download speeds are ~45MB/s. While this is great and all its not nearly the upload/download speeds I should be getting. I have multiple windows machines and I get 100MB/s+ from them. I&#8217;ve tried messing with the smb.conf file and tried suggestions from multiple sites. The only setting I generally mess with is &#8220;socket options&#8221;


Here is my current socket options:
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536


I&#8217;ve tried to enable jumbo frames. Tried both 9000 & 9014. I tried 9014 because that is the only packet size I can select for the network card in windows for 9k jumbo frames which really didn&#8217;t help at all. 


I&#8217;m kind of at a loss what to do. Any help would appreciated.

---

### Post by laszlo-janszky on 2017-09-01
If you mounted your smb with gvfs (not sure about current Ubuntu), then this is all you can get. There is a bug in the client: [https://bugzilla.samba.org/show_bug.cgi?id=10879](https://bugzilla.samba.org/show_bug.cgi?id=10879) I try to share this on many sites, maybe somebody fixes it. I don't speak C... You can try cifs mount from console or fstab instead, that is fast.

---

