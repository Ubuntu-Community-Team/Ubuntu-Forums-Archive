---
title: "Help with network printing setup"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by humbug01 on 2009-05-29
I have Jaunty on my desktop and I just replaced my wife's Apple laptop with an older Thinkpad so that I could load it with Ubuntu Jaunty also and make it easier to have a little home network for shared printing. On both computers I did a minimal install to a CLI and built it up from there with Gnome and other software I actually use.

My desktop has an HP deskjet printer attached (and it works fine with CUPS and the HP driver in the repository) and this computer is connected to the internet through a cable to my Belkin wireless router. The Thinkpad has wireless connection to this router (with the help of wicd) and I installed CUPS and the HP driver there as well.

The problem is that I have not been able to connect the Thinkpad to the printer through the wireless connection. I did use Avahi-discover on it and it did find the printer, but other than that no printing from the laptop.

I'd appreciate any hints or suggested tools to solve this little problem. Jaunty works very well on both computers so far, by the way.

Thanks in advance.

H.

---

### Post by superprash2003 on 2009-05-30
hope this helps [http://www.prash-babu.com/2008/05/how-to-setup-network-printer-or-share.html](http://www.prash-babu.com/2008/05/how-to-setup-network-printer-or-share.html)

---

### Post by humbug01 on 2009-05-30
Thank you for the link. It is helpful, but I have not installed Samba because I'm setting up a connection between two Ubuntu machines not Windows. Is Samba still the way to do this?

I should have noted above that I'm using gufw also on both machines and was wondering if that was preventing the host from letting the client connect.

Obvously I don't know much about networking computers....

---

### Post by salocinbake on 2009-05-30
Hi Humbug01,

I have a similar setup, yes samba is the way to go. But if you didn't edit your /etc/samba/smb.conf file don't worry it's pretty easy.

Go on your desktop pick a folder, right click, and select share. It will ask if you want to install samba. Just go with it.  Go the netbook and do the same. Don't forget to log out and log in again to get samba working.

After all this both computer should see each other.. Then go to System->admin->printing and setup the printing on your laptop.

Voila.

If you changed the workgroup in the smb.conf, they both have to be on the same.

Salo

---

### Post by superprash2003 on 2009-05-30
samba would still work..its easier to setup

---

### Post by cariboo on 2009-05-30
You don't need Samba to share a printer, there is an option in the cups interface to make the printer available to all coputers on the network.

See screenshot, you can access the cups interface by entering:

```
http://localhost:631
```

---

### Post by adrianx on 2009-05-30
I have a similar problem with two networked Linux machines (Jaunty/Mint). system-config-printer seems a bit broken in Jaunty at the moment. In Fedora 10, the setup is almost a no-brainer. All I have to do is click on "Shared" and open port 631 in my firewall (ipp) and Mint picks it up straight away.

Another problem that I have with system-config-printer 1.1.3 is that, sometimes, when I switch off my printer and switch it back on, it gets re-detected and added as a new printer.

Anayway, I will also try samba. (Not that I have a Windows machine anywhere near me...:D)

**Edit:** cariboo907, I didn't see your post. I've tried all of that today, the application and the cups web app. No luck. I also have an HP printer - don't know if that makes a difference.

---

### Post by humbug01 on 2009-05-30
Thank you all for your help.

Cariboo, your tip of going through CUPS via the http address did the trick. I had to open up port 631 in gufw and I did also set the printer in cups on the client machine but I printed out sample pages which worked perfectly.

Case solved!

Best regards,

H.

---

