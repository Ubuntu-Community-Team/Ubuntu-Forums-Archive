---
title: "OpenSSH-HPN for ubuntu 15.10"
date: 2015-11-15
forum: Networking &amp; Wireless
---

### Post by Spency on 2015-11-15
I'm trying to improve my data transfer speeds on my local network for a number of processes involving large file transfers. I stumbled upon [openssh-hpn]("https://launchpad.net/~w-rouesnel/+archive/ubuntu/openssh-hpn") which sounds right up my alley, but have only had success installing this patch on my 14.04 computers, it does not seem to install on 15.10 and I'm wondering if there is a work around for either installing the utopic or trusty tar versions of OpenSSH-HPN on newer Ubuntu systems, or for like disabling encryption for SSH manually - I have done a little digging around already for manually disabling encryption but haven't found anything that's relevant for Wily.

Thanks!

---

### Post by Spency on 2015-11-16
[SIZE=2][FONT=arial]So what I did was I tried downloading a patch from [http://www.psc.edu/index.php/hpn-ssh](http://www.psc.edu/index.php/hpn-ssh) and then manually piling it with the openssh source. [/FONT]

[FONT=arial]So I tried it with[/FONT] ```
git clone [FONT=monospace]git://anongit.mindrot.org/openssh.git[/FONT]
```
from [OpenSSH Portable]("http://www.openssh.com/portable.html")
[FONT=arial]
Installed libssl-dev , libpng-dev, and zlib1g-dev (Openssl is installed already)

Then I ran the following consecutively:
[/FONT][FONT=Helvetica Neue][FONT=arial]aclocalautoconfautoheaderautomake --add-missing

I've gotten through a lot of errors starting with the patch, leading to running configure and make, but now make seems to run for the most part but halts with:[/FONT]
[/FONT]```
channels.c: In function &#8216;channel_tcpwinsz&#8217;:channels.c:861:31: error: &#8216;BUFFER_MAX_LEN_HPN&#8217; undeclared (first use in this function)
  if ((ret == 0) && tcpwinsz > BUFFER_MAX_LEN_HPN)
                               ^
channels.c:861:31: note: each undeclared identifier is reported only once for each function it appears in
channels.c: In function &#8216;channel_output_poll&#8217;:
channels.c:2357:19: error: void value not ignored as it ought to be
     packet_length = packet_send();
                   ^
channels.c:2392:18: error: void value not ignored as it ought to be
    packet_length = packet_send();
                  ^
Makefile:152: recipe for target 'channels.o' failed
make: *** [channels.o] Error 1



```[/SIZE][COLOR=#333333][FONT=Helvetica Neue]
[/FONT][/COLOR]

---

