---
title: "Thunderbird timesout on SMTP send"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by NeuralEskimo on 2008-07-18
Thunderbird intermittently fails to send to our campus SMTP server and give a timeout message. However, I think the timeout is a red herring because: 
1) once Thunderbird fails, it continues to fail until closed and restarted,
2) other clients (Evolution) work fine while Thunderbird is failing,
3) the SMTP server has a long history of being quite reliable,
4) and everyone else has no problems.

I installed Thunderbird from the repositories, version 2.0.0.14 (20080505), and I am running Ubuntu 8.04 (Hardy Heron) and Gnome - all updates applied. I am connecting to the SMTP server via SSL.

Unfortunately, I am getting nothing else from Thunderbird. Any thoughts or advice on how to get Thunderbird to cough up more info.

---

### Post by NeuralEskimo on 2008-07-24
Replying to my own post...

The problem only appears when Thunderbird is started automatically at logon. In a nutshell, I have a logon script that is run by Gnome (listed in the startup programs in the sessions control panel). One other tidbit that seems relevant, I have a wireless laptop. My guess is that Network Manager doesn't have the wireless network fully up when Thunderbird starts (sometimes). The odd part is that I don't know why Thunderbird needs to contact the SMTP server on logon (I never have any queued email to send).

I suppose the obvious solution is to make the script sleep or wait for the network to come up before running Thunderbird.

Any other thoughts or suggestions?

---

