---
title: "Help my ubuntu-hardy loves bluetooth virus"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by mvalviar on 2008-12-15
Notes:

Ubuntu 8.04
Nokia 6600
cd-r-king bluetooth dongle (btd-609)
Using default gnome bluetooth utilities

Man, this sucks. I'm trying to browse my phone on my pc via bluetooth. I have my bt dongle connected and these devices paired but I can't see anything under obex://[mac address]/. It mounts because I can see it on my desktop and browse it through nautilus but there is nothing there. I can't receive files from my phone and my phone can't receive files from the pc. Even worse my pc is accepting files from the phone sent by a virus that I'm certain resides on my phone. Whenever I have an active connection between the phone and the pc I receive love.rm, beauty.jpg and sex.mp3 on my desktop. As I type this these files are populating my damn desktop! 

This is so wrong. I can't send/receive files to/from my pc/phone but the a virus can! What can I do to fix this? It gets worse because I tried to uncheck the "Receive files from remote device" minutes later there was a notification from the applet that "Recieve files from remote.." was enabled and I received yet another file.

I already tried with a clean Nokia 6600 I can't to anything with the bluetooth connection neither.

Here a pic> [IMG]http://mvalviar.freehostia.com/Screenshot.png[/IMG]

---

### Post by Viranh on 2008-12-15
This sounds like more of a problem with the virus on your phone than ubuntu and the blue tooth dongle. Do other blue tooth devices work with the dongle? Has the phone worked in the past? If the answer is yes, perhaps your service provider or the phone manufacturer can restore the phone's original software. Using google I stumbled on this guide to reset it yourself:
[http://raldztech.blogspot.com/2004/09/formatting-nokia-6600-phone.html](http://raldztech.blogspot.com/2004/09/formatting-nokia-6600-phone.html)

If it is a blue tooth problem, is there a specific error?

If you're having trouble with a non-infected Nokia, there may be some files that need to be purged left over from the infected one perhaps? You could try to remove completely/purge the package that communicates with mobile phones and pda's. I think it's listed in synaptic as "obexpushd." Maybe it's something else entirely, but I can't be sure.

---

### Post by mvalviar on 2008-12-15
I have no problem using the phones and the dongle with another pc running on xp. I can send/receive files to/from phone/pc without a problem. I can't browse the phone directly (I don't know how to) but at least I can use PC Suite to access the phone.

I'm guessing this can be fixed but I don't know what to do next. Because I tried to install other apps to access my phone (wammu, gnome-bluetooth etc) but none of them worked. 

On the clean phone I managed to receive a file from the pc but the pc still can't receive files from the phone Nor can the phone be browsed.

---

### Post by mvalviar on 2008-12-15
I just reformatted one of the infected phone. It still ain't working...

---

### Post by blue200316 on 2009-01-21
> **mvalviar said:**
> I just reformatted one of the infected phone. It still ain't working...

my dear frnd,ur phone have been infected by  Beselo.A and/or Beselo.B, u may visit f-secure site,they have the solution.

---

### Post by Thelasko on 2009-01-21
> **mvalviar said:**
> I can't receive files from my phone and my phone can't receive files from the pc. Even worse my pc is accepting files from the phone sent by a virus that I'm certain resides on my phone. Whenever I have an active connection between the phone and the pc I receive love.rm, beauty.jpg and sex.mp3 on my desktop. As I type this these files are populating my damn desktop!

That's a weird one.  To access the files on your phone I believe you need the obexftp package.  This doesn't explain why your machine is accepting files sent from the phone.  It should at least ask if you want to receive the files.

I would [file a bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-phone-manager") immediately and mark it a security issue.

---

### Post by mvalviar on 2009-01-22
I did a little research on this one. The virus is called baselo. I'm now able to receive files from my phone by downgrading bluez-utils. I already forgetten about this until now that you mentioned that I should file a bug report. I ready think I should have done that. But now I think its impossible to recreate it because I reformatted the phone. It really is weird because I haven't been able to receive anything from my phone until I downgraded bluez-utils. But by having my pc bluetooth on generates the files I mentioned on the desktop whats worse these files multiply on a 15 min interval as long a I have the bluetooth dongle connected.

---

### Post by Thelasko on 2009-01-22
> **mvalviar said:**
> I already forgetten about this until now that you mentioned that I should file a bug report. I ready think I should have done that. But now I think its impossible to recreate it because I reformatted the phone.
File it anyway, perhaps someone else will be able to recreate it.

---

