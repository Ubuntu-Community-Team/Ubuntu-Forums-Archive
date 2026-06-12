---
title: "Slow network still after disabling IPV6"
date: 2005-11-02
forum: Networking &amp; Wireless
---

### Post by REInvestor on 2005-11-02
I have just installed Ubuntu on an old IBM Thinkpad 600.  The network card I am using is a linksys pcm200.  The card was not detected during install, so I skipped network configuration at that point, but it was present (and disabled) once installation was complete.  I enabled it, but was unable to get an IP using DHCP until I searched the forums and found about the IPV6 "issue".  I did the following to /etc/modprobe.d/aliases

alias net-pf-10 off

After rebooting I am now able to get an IP, but it seems like it takes a very long time for this to happen during boot (>20 seconds).  I can access the internet with Firefox sometimes, but only partially. This is only after editing Firefox according to the forum:

[http://ubuntuforums.org/showthread.php?t=76096](http://ubuntuforums.org/showthread.php?t=76096)

I can get google to open up, but not really anything else, so I do technically have a connection, but AOL dialup would seem like light speed next to this.

Synaptics can not access the online packages, or just times out trying.

I will try to add other relevant info, but since I am not able to access this forum from the affected computer, copying and pasting terminal outputs is not possible.

Also - the IBM Thinkpad 600 had 2 other issues (for those searching for answers), the screen resolution kept coming up 800x600 and the sound does not work.  

The screen resolution fix was easy, but it took me hours to figure it out.  Get out of GDM with ctl-alt-backspace then reconfigure X using "sudo dpkg-reconfigure xserver-xorg" and do not change anything except color depth - which needs to be 16bit instead of 24bit.  I tried changing everything else in an attempt to fix this problem - which is why it took so long.  If I had only known.

The sound problem I think can be fixed with alsaconf but it is not included with the base system.  After fighting with sound on this laptop with numerous other distributions, I finally found out the BIOS quick boot needed to be disabled in order to get the sound working using the CS4236 driver.  If anyone has sound working on this machine without adding to the base packages, please let me know.

But, I can live with no sound for a time, no internet on the otherhand makes the laptop worthless.  Is it possible I have the wrong driver installed?  How can I check this or correct that type of problem?

---

