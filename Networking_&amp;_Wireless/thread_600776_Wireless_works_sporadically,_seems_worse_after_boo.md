---
title: "Wireless works sporadically, seems worse after boot to XP"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by racekarl on 2007-11-02
I've tried searching, but unfortunately wireless problems with ubuntu seem to be rampant, so it's hard to sort through what's relevant and what's not.

My main problem is that ubuntu will almost never connect to my wireless AP on startup.  Sometimes I can get it to connect after a reboot, and sometimes by opening the network configuration app and toggling between network locations (Home and Work, oddly neither is selected at boot time), but sometimes none of these work and I have to give up and boot to XP (which always works).

My computer is a Thinkpad T42 with (I think) an Atheros-based wireless card.  I know the network is properly configured and the WEP key and all that is correct, because it does sometimes work.

The problem seems to be worse if I had booted XP on the previous boot; if I had it working in ubunutu, and shut down and reboot back into ubuntu, it usually works on start up.

I'm a n00b, so please forgive the lack of detail. I'll gladly post any additional details if needed  (e.g. lspci or what have you).

---

### Post by jnorthr on 2007-11-02
just a thought on this, do you power off between each boot ? Just wondering if the interface card maybe is retaining some previous settings from the prior o/s programming it if you don't power down...

---

### Post by racekarl on 2007-11-07
Thanks for the reply.  Unfortunately, cold and warm boots produce the same result.

It has definitely gotten much worse, and now just does not work at all.  No amount of rebooting or changing network locations allows me to connect to my wireless network.

Some other things I noticed:

The network monitor icon on the task bar shows now connection for adapter ath0.  However, if I open the properties window, the entries that appear in the list are lo and ath0:ahvi (or sometyhing like that, I'm doing this from memory since I can't post from ubuntu obviously).

Also, if, with ath0 selected in the interface text box, I click the "Configure" button, it will sometimes show an error message that the interface does not exist.  Othe times it will show the wireless configuration dialog as expected, with all the correct information.

---

