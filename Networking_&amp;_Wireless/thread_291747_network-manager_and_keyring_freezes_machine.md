---
title: "network-manager and keyring freezes machine"
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by Ares139 on 2006-11-02
Hello, I'm rather new to Ubuntu, and was having wireless issues with the normal networking interface.  The connection kept getting dropped so I thought I would try network-manager-gnome.  After installing it, I rebooted the machine, and then logged back in and configured network-manager-gnome to use my WEP password.  However, then it asked for the default keyring password, and everything froze.  I could see the system monitor applet running on my top panel - the system wasn't really frozen, but I couldn't click or type anywhere.  I know it's *supposed* to do that when it prompts for the password, but the problem is, the password prompt is *also* frozen.  So I couldn't type anywhere at all.  I had to ctrl+alt+backspace and restart X, which partially worked but then it hung when I tried to log in.  I restarted X again, and then rebooted the machine at the login screen.  Fsck decided to run while booting, and it froze.  Just showed the fsck version number and sat there.  I could type things it seemed, but there was no disk activity whatsoever.  So I rebooted.  This time I logged in fine, and fsck didn't run.  I tried configuring network-manager-gnome again, but the password prompt froze yet again, so I rebooted, and this time fsck ran because it was the 30th mount.  Fsck completed successfully this time, and I booted back up.  I managed to get it online, but I'm not sure what I did wrong, and I'm not sure why the keyring prompt freezes like that.  If I go to the Keyring Manager it prompts for the password like it should, and I can type in it there.

I'm not sure if I should attempt to remove the network-manager and use the normal Ubuntu manager, or if I should just leave it like it is since it's currently working.  The problem is if I try to configure anything in it, the keyring prompts and freezes and I have to reboot.  Seems a little buggy to me.  I used this manager on Dapper before without incident.  Not sure what I've done wrong.

Any suggestions would be greatly appreciated.  The whole fscking and not booting alarmed me at first.  I have no problems fixing a Windows box that won't boot up, but I haven't the foggiest idea how to get Ubuntu back up if it won't boot.  I'm just trying my best not to break anything lol


-Ares

---

