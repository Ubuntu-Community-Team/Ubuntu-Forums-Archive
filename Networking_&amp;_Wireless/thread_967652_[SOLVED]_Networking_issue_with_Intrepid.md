---
title: "[SOLVED] Networking issue with Intrepid"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by mmm2010 on 2008-11-02
I just installed 8.10 on my desktop computer, and it's not connecting to the internet.  I have a wired ethernet connection running from my computer to my router to my modem.  When I click on the network applet, I see the connection "eth0," but when I click on it it doesn't work.  Both dots turn green, but it never connects and after about 30 seconds it shows a message saying that the network has been disconnected.

Since it recognized the eth0 connection, I was thinking it wasn't a driver issue, but I don't know for sure. Do I need to manually set up the connection, or what?

Thanks for any ideas.

---

### Post by widor on 2008-11-02
Using Terminal, type in the following command:

    ping -c 4 91.189.94.12

Wait for it to finish and when it gives you the "ping statistics", see what percentage it shows for packet loss. If it's less than 100% then try this command instead:
    
    ping -c 4 ubuntuforums.org

If you now get something like "unknown host ubuntuforums.org" then look at the contents of your /etc/resolv.conf file using the following command:

    cat /etc/resolv.conf

Does it contain a line starting with the word nameserver? If not then add a line like the following:

    nameserver 192.168.0.1

but replacing 192.168.0.1 with the IP address of your usual name server (your ISP should be able to tell you this if you don't already know it). Hopefully you should then find that internet connections work, at least until you next reboot.

To avoid the problem returning after you reboot, make sure that you have the resolvconf package installed (using System -> Administration -> Synaptic Package Manager and then type resolvconf in the "Quick search" box).

---

### Post by felipefrog on 2008-11-02
I have the same issue here, but on my eeepc 701 though.

It detects wireless connections, but never connect. Same thing with wired router.

---

### Post by mmm2010 on 2008-11-02
I'm not sure why, but when I was doing that and I rebooted, it finally connected.  I have no idea why, since I had already rebooted before that several times, but it's working now.

Thanks for the ideas, though, widor.  Maybe someday I'll begin to understand all that command line junk myself, but for now I know very little... 

I've seen that a lot of other people are having issues with wired connections, though, after upgrading.  Do you think it's just a bug that they'll fix, or is it just a hit-and-miss compatibility issue that can't be dealt with?

---

