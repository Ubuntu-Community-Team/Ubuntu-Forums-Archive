---
title: "Nautilus and samba"
date: 2024-04-03
forum: Networking &amp; Wireless
---

### Post by deck on 2024-04-03
I recently upgraded my 20.04 LTS to 22.04 LTS.  I am usning the Gnome Classic interface both because I like it and it works better on the older hardware I am using (it is an affordability issue).  When it was first installed 22.04, I could go through Nautilus - Other Locations, type in smb://192.168.x.x to access a windows computer on my network.  Now if I type in smb://... the text turns red and nothing happens.  I have reinstalled samba and samba-client to no effect.  It is still doing the same thing.

Something that might be related to this is when I click on Places>Network I get a pop-up with the message -- **Could not open location 'network:///'**.

As I think back this all occurred after I installed wine32 which I need for some Amateur radio programs that I run.  wine32 required some library that I had to go back and install.  When that library was installed funny things started to happen.

Note:  After posting I went and installed wine64.  It required libgd3.  So I apt-get install libgd3.  As I watch wine32 is uninstalled and wine64 is installed after getting the library.  I tried things out and they are still broken.  So I went back and installed wine32 with libgd:i386.  This may have nothing to do with the issues I am having.

---

### Post by Morbius1 on 2024-04-04
Looks like you have one and possibly two different problems here.

The "could not open .." appears to be a broken or missing package. Install it:
```
sudo apt install gvfs-backends
```

The other issue relates to a years long design flaw in gnome related to how it "browses" the network for hosts instead of "discovering" them.

If **[COLOR="#0000FF"]smb://192.168.x.x[/COLOR]** doesn't work address the server AND it's share explicitly: **[COLOR="#0000FF"]smb://192.168.x.x/share-name[/COLOR]**

*Note: How wine affects any of this I do not know as I don't use it.*

---

### Post by deck on 2024-04-10
Morbious1, That worked. I had to remove wine32 which involved removing libgd:i386 and libgphoto:i386.  Those latter two files had to be the libgphoto:64 and libgd:64.

I will have to find another way to install wine32 to run amateur radio programs.

---

