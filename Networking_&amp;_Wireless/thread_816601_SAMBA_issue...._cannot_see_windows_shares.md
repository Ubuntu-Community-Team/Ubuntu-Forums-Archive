---
title: "SAMBA issue.... cannot see windows shares"
date: 2008-06-02
forum: Networking &amp; Wireless
---

### Post by nanohead on 2008-06-02
Hardy, 8.04, running great.  I can mount the Hardy shares from the windows side, no problem.  Can browse and perform file operations from the Windows machines on the samba shares running on Hardy

But the other way does not work at all.   There are no error messages, and I can see the workgroup, but when I click on it in Gnome "windows network - file browser", I see nothing.  Using WFWG, no domains or any fancy stuff.  Just peer to peer.

Makes no sense.  It seems like every release, there is one direction of samba that does not work, and I never know which one it will be.:confused:

---

### Post by Iowan on 2008-06-03
Can you see the machines (just not the shares) or is the workgroup empty?  If it's an empty workgroup, then you may need to setup Samba as a WINS server (which one thread said CAUSED problems) or install/use Winbind.  Another option is to setup Samba as Master Browser.  In brief - *something* needs to provide a list of available NETBIOS names for Ubuntu.

---

### Post by Prospero2006 on 2008-06-03
I'm not sure what you've tried.

Try this:
```

smbclient -L ip_addy_of_windows_box

```

anything?

---

### Post by geoff511 on 2008-06-03
Hi Nanohead,
Had the same problem as you, found the answer on the How-To Geek page :

[http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)

Tells you step-by-step how to set up Samba. Windows then sees Ubuntu & Ubuntu sees windows,  just don't forget to share a folder or two on both machines first, seems to help, as necessary settings are then in place.

Hope that helps.

---

### Post by nanohead on 2008-06-03
Thanks for all the great replies and ideas.   I did manage to hack my way through some things, some which make no sense, others which do.

There appear to be some issues on both the Windows and the Ubuntu side.   The Windows issues relate to how Vista shares folders, which has a few more layers than XP does.   I was able to fix that pretty quickly in Vista.   I had to create a new share alias (a pseudonym for the existing folder, which you could do in XP also), and then set permissions to everyone do everything.   Also to make it visible, you have to make some changes in the Vista network and sharing screen.   Its not just setting the folder to share anymore.  So the Vista part was pretty straight forward.

The Ubuntu part is somewhat more frustrating, and seems consistent with the other changes that were made to sharing and Samba in Hardy (most of which are terribly thought through unfortunately).  I just don't know what the guys who worked on this were thinking.

It seems that just setting up Samba via .conf or SWAT is not enough now for bi-directional browsing and file operations.  I rummaged around for a while, and ended up in the Network Settings tool, which showed in the General tab, different host name and domain name settings that those of smb.conf/SWAT (this is ridiculous and spastic)

You have to change the host name and domain name in the Network Settings tab to reflect what is in smb.conf (why they are not synced, is anyones guess, as Suse and FC do not have this problem).   When you change them, the whole thing just starts working.   But now the even more ridiculous part, is that the settings do NOT remain persistent after a reboot, which is shabby.   Argh....:mad:

I switched from FC over to Ubunutu about 18 months ago, it seemed more lightweight and simpler.  But with each new release, I've had to do major surgery to get the thing to work like it worked before the "upgrade".   Now there are lots of arbitrary changes being made, and if one submits a bug, one gets a curt, snotty response to the issue from some dev, who thinks you are dumb.

When a new FC and Suse come out, I load them too just to see what those guys have done, and they are progressing FORWARD in most cases.  The Ubuntu thing is in need of some serious adult supervision IMHO

ADDED:  I figured out why the host name and domain name persistence was failing.   In the network settings tool, on the Connections tab, if you open your default network properties (wired in my case), the default setting is for Enable Roaming mode.  (why this is is anyones guess).  If you uncheck that box and disable roaming mode, then below it check to enable DHCP, the thing starts working properly and the settings are persistent after a reboot.   Silly and sloppy...    :confused:

How would anyone with limited knowledge figure this stuff out.   I just scrapped Hardy off my laptop (a plain jane IBM T23), because nothing worked right after 3 installs and weeks of hacking.   Argh

---

