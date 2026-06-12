---
title: "UDP multicast stream - RTP protocol source"
date: 2014-06-07
forum: Networking &amp; Wireless
---

### Post by zedi on 2014-06-07
My IP provider is  broadcasting IPTV for members only which I can watch in Firefox on Windows via VLC plugin. As far as I know its UDP multicast stream via RTP. 
Unfortunately I can't do that in my Ubuntu Precise and Cinnamon Mint 15. 
Message in Firefox: "totem-plugin-viewer can't find required plugin - RTP protocol source".
I tried to open stream in VLC - "VLC is unable to open the MRL 'https://www.tpg.com.au/iptv/iptv_viewer.php'." was the result. 
When I open in VLC playlist from my provider nothing happens.
I even installed Firefox and VLC in Wine but no luck. Firefox says "VLC plugin is not working".
When I contacted IP support the answer was **its a Linux not them**.
I'm getting rid of dual boot and be Linux only as I believe somebody with Linux knowledge will help me.

---

### Post by tgalati4 on 2014-06-07
There is a message and error console in VLC.  Try opening in VLC and see what the specific error messages are.  You can also try *mplayer URL* and see what comes up.

---

### Post by zedi on 2014-06-08
Hi tgalati4,
Problem is error console is Chinese to me.
VLC says: Check the log for details but I can not find any log (looked in config and local/share).
Found VLC messages:
gnutls error: TLS session: access denied
gnutls error: Certificate could not be verified
main error: TLS client session handshake error
access_http error: cannot establish HTTP/TLS session
main error: open of `[https://www.tpg.com.au/iptv/iptv_viewer.php](https://www.tpg.com.au/iptv/iptv_viewer.php)' failed

MPlayer log:
/usr/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xv -ao pulse -nokeepaspect -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 77594659 -monitorpixelaspect 1 -ass -embeddedfonts -ass-line-spacing 0 -ass-font-scale 1 -ass-styles /home/zmint/.config/smplayer/styles.ass -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp UTF-8 -subpos 100 -volume 89 -cache 2048 -osdlevel 0 -prefer-ipv4 -vf-add screenshot -noslices -channels 2 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 [https://www.tpg.com.au/iptv/iptv_viewer.php](https://www.tpg.com.au/iptv/iptv_viewer.php)
MPlayer svn r34540 (Ubuntu), built with gcc-4.7 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.
Playing [https://www.tpg.com.au/iptv/iptv_viewer.php](https://www.tpg.com.au/iptv/iptv_viewer.php).
No stream found to handle url [https://www.tpg.com.au/iptv/iptv_viewer.php](https://www.tpg.com.au/iptv/iptv_viewer.php)
Exiting... (End of file)
ID_EXIT=EOF

In windows I can watch stream in browser but first i have to log-in. When I try to log-in in Linux it tels me VLC and web browser plugin is to old (attached screen-shot) which is odd my version is 2.0.8 and plugin 2.0.0-2. When I click OK totem looks for plugin and tels me couldn't find RTP protocol source.
When I open a playlist after login in browser:
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.
Playing rtp://@233.29.121.110:1234.
STREAM_RTP, URL: rtp://@233.29.121.110:1234
Timeout! No data from host 233.29.121.110
rtp_streaming_start failed
No stream found to handle url rtp://@233.29.121.110:1234
Exiting... (End of file)
ID_EXIT=EOF

and from VLC messages: 
main info: stopping playback

BTW in Gufw I allowed UDP port 1234 IN from anywhere and forwarded this port in router.
Windows can see the stream and can play it. Why Linux can not?

---

### Post by zedi on 2014-06-15
Some more info. To watch IPTV you have to configure the router.
    Create a new connection in the modem user interface
    Service name: IPTV
    Connection/Mode: bridge mode
    Encapsulation/Multiplexing: LLC
    VPI: 0
    VCI: 35
    ATM/QoS: UBR
    PVC: enabled
    An option for IGMP proxy, or multicast proxy should be enabled

My router come preconfigured by ISP, in WAN section it has 2 interfaces: atm1 - Bridge and ppp0 - PPPoE.
The problem as I see it, is that I can't log-in @ browser. Would it be VLC plugin integraton in browser?
I hope this will bump the topic.

---

### Post by zedi on 2014-06-20
Just in case somebody will have similar problem, I installed Mint 17-Qiana and uninstalled "totem-mozilla" (requirement, "mint-plugin-codecs" have to go as well). Than I installed "browser-plugin-vlc".
Now I can watch IPTV which my ISP provides for free.
I hope the same will happen when I upgrade to Trusty.

---

