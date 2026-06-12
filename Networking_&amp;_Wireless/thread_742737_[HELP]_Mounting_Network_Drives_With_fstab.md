---
title: "[HELP] Mounting Network Drives With fstab"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by Pyro.699 on 2008-04-02
**This post could be related to an Ubuntu bug filed at**: ve [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello,

I have networked a shared folder between my Ubuntu Hardy 8.04 and Windows XP Computers successfully, and there seems to be only one problem, i can only mount 1 drive, and not the entire share its self... heres what i have

```

//Bulbasaur/media	/media/Bulbasaur	smbfs	rw	0	0

```
(Yes all my computers are named after pokemon xP)

heres something close to what i am trying to achieve

```

//Bulbasaur	/media/Bulbasaur	smbfs	rw	0	0

```

so that just the root directory of the share is mounted... because i  do have several shared folders on 1 computer (I would prefer to stay away from dragging all those folders to the main share folder on the windows xp computer if possible thank you)

Thanks for all your help
~Cody Woolaver

---

### Post by Pyro.699 on 2008-04-03
Sorry for bumping but this is somewhat of an important topic because without it, it is much more difficult to mount and access my remote drives. Thanks

---

### Post by Eiríkr on 2008-04-03
The smbfs filetype has been deprecated for some time and was finally phased out somewhere around Samba v3.024 or v3.026 (possibly even earlier).  v3.026 is currently the default package for Ubuntu Gutsy.  You'll have to use the cifs type instead.  Moreover, you need to familiarize yourself with the various mount options for the cifs filesystem type, by entering [font=courier]man mount.cifs[/font] in a terminal.  

That aside, what do you mean "i can only mount 1 drive, and not the entire share its self"?  The first example you show with the Samba path //Bulbasaur/media ***is*** the entire share -- the share is the "media" portion of this path, and "Bulbasaur" is the server name.  If you're trying to share the root of a drive, set that up as a share.  In XP, for instance, once you enable sharing, the whole C: drive is shared by default (unless you explicitly un-share it) "for administrative purposes", whatever the heck that's supposed to mean (sounds like Microsoft-ese for "we like exposing everyone to the biggest security holes we can think of -- so there, nyah nyah!").  If you want to share a full drive in XP, open Explorer, right-click that drive's icon, and select "Sharing and Security", and Bob's your uncle.  

Cheers,

Eiríkr

---

### Post by Pyro.699 on 2008-04-03
Lol, thanks. But you somewhat made it unclear as to what it is hat i need to do, i know that there are major securety holes in letting people see your entire c: (Remembering there are some dirs that even if you share you cannot access). Where exactly do i need to go and what do i need to chane/add inorder to get this to work. Thanks

---

### Post by Eiríkr on 2008-04-03
Literally, just like I said at the end of my post: open Explorer, right-click any (non-mapped) drive's icon, and select "Sharing and Security".  The dialog that pops up should make things pretty clear.  

Cheers,

Eiríkr

---

### Post by Pyro.699 on 2008-04-04
Not in windows, im fine navagating windows and its properties. Im unable to mount **//bulbasaur** but i can mount individual folders. thanks

---

### Post by Eiríkr on 2008-04-04
As I tried to describe above, //bulbasaur is not a share, it is the server.  You can't mount a server, as it's not a filesystem.  You can only mount filesystems.  The drives on the server are (or strictly speaking, contain) filesystems, so you can share those on the XP side, and then mount them on the Ubuntu side.  Does that help clarify things at all for you?

Cheers,

Eiríkr

---

### Post by Pyro.699 on 2008-04-04
Yes it does, thankyou for explaining it again. Am i to asume there is no way around this?

---

### Post by Eiríkr on 2008-04-04
I'm not sure I understand what you mean by "a way around this" -- I'm confused as to what limitation you've perceived that needs working around.  :confused:

---

### Post by Pyro.699 on 2008-04-04
setting the server as a mount

---

### Post by Eiríkr on 2008-04-04
Allow me to repeat: 
[list=1][*]**You can only mount filesystems.  **
[*]**The server is not a filesystem.**
[*]**Therefore, you cannot mount the server.**[/list]
Is that clearer?

I must admit I'm quite befuddled by your desire to mount "the server", and I'm not even fully sure I understand what you mean by that.  The server is a machine, a computer, which most likely has in it at least one hard disk and possibly several.  If you want, it's totally possible to share and then mount any of the hard disks on the server; but the server itself includes all kinds of things that are not filesytems -- things like monitors, mice, keyboards, video cards, NICs, and so forth.  It simply wouldn't make any sense to "mount" any of these, which is precisely why they aren't mountable.  **You can only mount filesystems.**  

Cheers,

Eiríkr

---

### Post by cmunic8r on 2008-04-06
> **Eiríkr said:**
> Allow me to repeat: 
[list=1][*]**You can only mount filesystems.  **
[*]**The server is not a filesystem.**
[*]**Therefore, you cannot mount the server.**[/list]
Is that clearer?

I must admit I'm quite befuddled by your desire to mount "the server", and I'm not even fully sure I understand what you mean by that.... *snip*  It simply wouldn't make any sense to "mount" any of these, which is precisely why they aren't mountable.  **You can only mount filesystems.**  

Cheers,

Eiríkr

 
He's trying to have the machine create a 'link' that, when opened, shows all the shares on a particular remote system.  a launcher on the desktop would provide a limited solution.  He's trying to use fstab to do the same thing because unless the destination is mounted, you can't normally use the launcher as a save destination for files.

the only way I know how to do this is to add a location to Places.  it doesn't help if you are trying to use it in a terminal window, but it should help when you're using X.

I would recommend doing something similar to this (these steps work for Gutsy in Gnome) 

On the panel, click Places, Connect to Server.
In Service type, select Windows share
In Server type the name or IP of the server
In User Name put the username you want to use at connect
in Domain name put in the appropriate domain or workgroup name
In Name to use for connection, call it whatever you want

if you open gedit or another program you should now see the name you used for the connection on the left of the window under Places when you try to save or open a file.

(if you wanted to save a file in gedit, for example, you can't pick a launcher on the desktop to open a link to a remote share)

---

