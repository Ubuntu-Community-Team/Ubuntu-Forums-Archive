---
title: "failing to install samba"
date: 2017-07-17
forum: Networking &amp; Wireless
---

### Post by jgw on 2017-07-17
I have been trying to install samba but I get an error no matter what I do.  The installation log is at: [https://pastebin.com/GSbj82js](https://pastebin.com/GSbj82js)

This all started when I was trying to set up samba and decided that I had truly screwed it all up so I decided to reinstall.  What I really need are, basically, two things.  The first is how to completely remove samba.  At one point I did the purge thing and then found every samba file left on my drives and deleted those too.  Anyway, after I actually get rid of everything I need to know if the sudo apt install samba is enough or there is something else I should be doing.  I have read all sorts of stuff about installing and, it seems, everybody has a different way.  Anyway ..................

The first thing I did was: 

apt-get remove --purge samba samba-common  I should mention that I have been at this for a while and have used several ways to delete it all but this seemed likely to do that best.  After my last failure I also did the following:
greg@greg:~$ systemctl status smbd.service
&#9679; smbd.service - LSB: start Samba SMB/CIFS daemon (smbd)
   Loaded: loaded (/etc/init.d/smbd; bad; vendor preset: enabled)
   Active: failed (Result: exit-code) since Mon 2017-07-17 15:37:21 PDT; 6min ag
     Docs: man:systemd-sysv-generator(8)

Jul 17 15:37:21 greg systemd[1]: Starting LSB: start Samba SMB/CIFS daemon (smbd
Jul 17 15:37:21 greg smbd[24508]:  * Starting SMB/CIFS daemon smbd
Jul 17 15:37:21 greg smbd[24508]: /usr/sbin/smbd: error while loading shared lib
Jul 17 15:37:21 greg smbd[24508]:    ...fail!
Jul 17 15:37:21 greg systemd[1]: smbd.service: Control process exited, code=exit
Jul 17 15:37:21 greg systemd[1]: Failed to start LSB: start Samba SMB/CIFS daemo
Jul 17 15:37:21 greg systemd[1]: smbd.service: Unit entered failed state.
Jul 17 15:37:21 greg systemd[1]: smbd.service: Failed with result 'exit-code'.

greg@greg:~$ journalctl -xe
-- Support: [http://lists.freedesktop.org/mailman/listinfo/systemd-devel](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)
-- 
-- Unit acpid.service has finished starting up.
-- 
-- The start-up result is done.
Jul 17 15:37:24 greg sudo[23358]: pam_unix(sudo:session): session closed for use
Jul 17 15:37:35 greg org.gnome.zeitgeist.SimpleIndexer[1442]: ** (zeitgeist-fts:
Jul 17 15:38:03 greg gnome-session[1587]: [GFX1-]: ClientLayerManager::BeginTran
Jul 17 15:38:03 greg gnome-session[1587]: LOADEEDD CS: [https://mychartwa.provide](https://mychartwa.provide)
Jul 17 15:38:03 greg gnome-session[1587]: [GFX1-]: ClientLayerManager::BeginTran
Jul 17 15:38:03 greg gnome-session[1587]: [GFX1-]: ClientLayerManager::BeginTran
Jul 17 15:38:18 greg kernel: [UFW BLOCK] IN=enp2s0 OUT= MAC=01:00:5e:00:00:01:40
Jul 17 15:38:49 greg gnome-session[1587]: LOADEEDD CS: [https://pastebin.com/logi](https://pastebin.com/logi)
Jul 17 15:38:50 greg gnome-session[1587]: LOADEEDD CS: [https://pastebin.com/u/jw](https://pastebin.com/u/jw)
Jul 17 15:39:02 greg gnome-session[1587]: LOADEEDD CS: [https://pastebin.com/](https://pastebin.com/)
Jul 17 15:39:23 greg org.gnome.zeitgeist.SimpleIndexer[1442]: ** (zeitgeist-fts:
Jul 17 15:39:42 greg gnome-session[1587]: LOADEEDD CS: [https://pastebin.com/GSbj](https://pastebin.com/GSbj)
Jul 17 15:40:15 greg gnome-session[1587]: LOADEEDD CS: [https://ubuntuforums.org/](https://ubuntuforums.org/)
Jul 17 15:40:19 greg gnome-session[1587]: LOADEEDD CS: [https://ubuntuforums.org/](https://ubuntuforums.org/)
Jul 17 15:40:23 greg kernel: [UFW BLOCK] IN=enp2s0 OUT= MAC=01:00:5e:00:00:01:40
Jul 17 15:40:25 greg gnome-session[1587]: LOADEEDD CS: [https://ubuntuforums.org/](https://ubuntuforums.org/)
Jul 17 15:42:28 greg kernel: [UFW BLOCK] IN=enp2s0 OUT= MAC=01:00:5e:00:00:01:40
Jul 17 15:44:33 greg kernel: [UFW BLOCK] IN=enp2s0 OUT= MAC=01:00:5e:00:00:01:40

Thank you......................

---

### Post by jgw on 2017-07-22
I continue fighting this one.  Here is the results of an attempt to install samba: [https://pastebin.com/fbVyVj6K](https://pastebin.com/fbVyVj6K)  yet again (have tried everything I could find - I have removed and installed about 30 times)

This is something to do with my system but I can't figure it out.  I get the same errors no matter what.  I have now installed samba on 3 other machines with no problem at all but this one is giving me fits.  I have also tried every uninstall routine anybody has suggested and nothing fixes it so its something on my machine.  I have also noticed that there are no replies to this and, in my search, I found several others, similiar to mine, that are also not answered.  This usually tells me that there is something laying out there that I should know but, for the life of me, I can't find it.  

My only other option is to save what I can and simply reinstall ubuntu on the drive and have a clean install.  If anybody has thoughts on this one I would REALLY appreciate it!

Thank you.....................

---

### Post by Morbius1 on 2017-07-23
I suspect the reason most folks are not responding to your post is the way you attempted to resolve your issue:
> At one point I did the purge thing and then found every samba file left on my drives and deleted those too.
It's the "found every samba file" part of the quote that keeps me away.

> This all started when I was trying to set up samba and decided that I had truly screwed it all up so I decided to reinstall.
No matter how long one has been away from Windows the instinct to reinstall something when it doesn't work persists. In the case of Samba in particular it's unnecessary.

Samba prevents the user from modifying the internals of how samba works except for one file: /etc/samba/smb.conf. It is not what the man pages call "The configuration file for the Samba suite". It is a file that allows the overlay of adds or overrides to the default settings ( which the user has no access to ) of samba. When samba runs it takes the defaults then checks smb.conf to see if there are any updates and then creates a samba instance.

If you mess up smb.conf there is a factory fresh copy of it located at: /usr/share/samba/smb.conf . You can copy that to /etc/samba, restart smbd and nmbd, and you are reset.

If it were me at this point I would reinstall your OS.

---

### Post by jgw on 2017-07-23
thanks for the reply.  I am curious.  Why doees it bother that I examined my machine and deleted every samba file I could find (other than music sambas <G>)  When I have deleted samba I also made sure that I got rid of the smb.conf fine in user/share/samba, etc/samba, and, sometimes, /.local/share/Samba.  None of the things to remove samba does it, ie. sudo apt remove samba, sudo apt remove --auto-remove samba, sudo apt purge samba.  When I searched my system for samba files I found not one or two but well over 100!   My present problem is that I simply cannot get it to install.  Given this happens no matter what, and that I know there are no samba files left over, I suspect my basic system.  

I also agree, reinstall the entire sytem is the way to go as the error remains exactly the same and nothing I could find could tell me what was wrong (other than ubuntu always tells me that the system screwed up and do I want to send a report which seems to be happening with some regularity).

Anyway, thanks again for the reply.  I am going to mark this as done/solved and move on <G>

---

