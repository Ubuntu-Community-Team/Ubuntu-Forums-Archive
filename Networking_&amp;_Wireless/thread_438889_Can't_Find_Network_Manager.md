---
title: "Can't Find Network Manager"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by Pablo Phoenix on 2007-05-10
Hi guys. I've been using Feisty for a while now, and I've run into a little problem. I acciddentally removed the Network Manager from my toolbar, and now i simply cant find how to put it back. The network manager available to put back is the old one from Edgy.... I'm kinda stuck...

Thanks guys!

Keith

---

### Post by renzokuken on 2007-05-10
just right click on the panel and select "add to panel". you should find it in the window that comes up. just drag it across

---

### Post by Kobalt on 2007-05-10
I don't think Network-Manager is in the "Add to the panel" menu, you need to launch it back using Alt+F2 and then *nm-appler --sm-disable*
Make sure you also have this into System > Pref. > Session : programs at startup so that it launches automatically at startup.

---

### Post by Pablo Phoenix on 2007-05-10
This nm-applet is still running, but the icon on the toolbar is gone. I followed your instructions, but to no avail.

---

### Post by c0reyf on 2007-05-10
I'm having kind of the same problem as I can't see the "correct version" of network manager running. I only have the option that shows up in my panel is the Manual Network Configuration? My  network manager has disappeared? ANy ideas? I do have the command above in my session for startup but it comes up as manual only.

---

### Post by c0reyf on 2007-05-10
Bump

---

### Post by Pablo Phoenix on 2007-05-15
Bump

---

### Post by NilsE on 2007-05-15
If nm-applet is still runing then just do an "add to panel" for the notification area and the icon should come back.  

If not then put nm-applet in the sessions startup and it should also come back with the notification area on the panel.

---

### Post by c0reyf on 2007-05-15
I found out that if you make any manual settings it will take your wireless networks and vpnc out of the network icon. The Icon will show up but you can't make any VPN or Wireless selections only manual settings. I went  into the manual and removed all settings to nothing and my VPNC and network manager came back. Just in case anyone runs into this. Thanks for your reply.

---

### Post by kswenson on 2007-05-15
I've added the nm-applet to the session startup.  It starts up now but always asks for a password...
   does anyone know how to make it so the password is not necessary.

---

### Post by NilsE on 2007-05-15
> **kswenson said:**
> I've added the nm-applet to the session startup.  It starts up now but always asks for a password...
   does anyone know how to make it so the password is not necessary.

You may need to add gksudo in front of the nm-applet but I also believe keyring will handle that for you so look in the Synaptic repository and install libpam-keyring which it sounds like it already is but make sure.

Then go into terminal and run

sudo echo "@include common-pamkeyring" | sudo tee -a /etc/pam.d/gdm

 This will allow you to remember connection passwords/keys in the keyring
and not get prompted by the keyring manager every time.

---

### Post by kswenson on 2007-08-06
thanks for the reply...
   this was already done.
it does only ask me for  a password when i boot up...
   my problem is that i simply want no password, EVER.

---

### Post by juamez. on 2007-10-13
> **c0reyf said:**
> I found out that if you make any manual settings it will take your wireless networks and vpnc out of the network icon. The Icon will show up but you can't make any VPN or Wireless selections only manual settings. I went  into the manual and removed all settings to nothing and my VPNC and network manager came back. Just in case anyone runs into this. Thanks for your reply.

YAY, that fixed it for me. I love you.

My problem was: I was fiddling around with vpnc and stuff, and when that was installed, the wireless connections were gone from my tray icon left-click menu. I then went into "**** this"-modus and uninstalled vpnc and it's GUI, but to no avail. I now deleted every entry that could be deleted from the manual configuration in every possilble tab, and BAM all is back again.

Coming to this forum has beared its fruits afterall.

---

### Post by diafygi on 2007-10-23
> **c0reyf said:**
> I'm having kind of the same problem as I can't see the "correct version" of network manager running. I only have the option that shows up in my panel is the Manual Network Configuration? My  network manager has disappeared? ANy ideas? I do have the command above in my session for startup but it comes up as manual only.

I ran into that problem as well. The key is adding the "Notification Area" to the panel. I posted about it [here]("http://ubuntuforums.org/showpost.php?p=2686815&postcount=8").

---

