---
title: "Wireless, not connected at boot."
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by Zwendel on 2008-01-10
Hi all,

I'm having some trouble with my Linksys WPC54G v1.2 wireless pcmi card.

Using part of these instructions:
[http://ubuntuforums.org/showthread.php?t=340689](http://ubuntuforums.org/showthread.php?t=340689)

but then with the linksys drivers of course, I managed to get it up and running yesterday. But now I have two problems.

When I boot, there is no wireless device available. I don't see my wlan0 when checking with iwconfig.
 I have to repeat these two lines in command line each time I boot, then the wlan0 becomes active.

```
sudo depmod -a
sudo modprobe ndiswrapper
```

Plus, each time the keyring manager asks me for a password so it can access the wep key.

Is it possible to make this connection permanent? I mean that the wireless card is recognized on boot and the connection defaults to my home wireless network without the keyring asking me for a password each time?

On top of all this, unlike when I was connected via wired network, windows xp no longer recognizes the hostname of my ubuntu laptop. I used to be able to connect to it using the hostname, now I have to use the IP address, although if I check my router, there the hostname is visible amongst the connected PC's. 

How do I solve these two issues. Thanks for your help!

---

### Post by wieman01 on 2008-01-10
Try this:
> echo 'ndiswrapper' | sudo tee -a /etc/modules
Then reboot.

---

### Post by Zwendel on 2008-01-10
> **wieman01 said:**
> Try this:

Then reboot.
Ok, I just tried that, but no success. Still no wireless device after reboot unless I execute those 2 lines + the keyring password

---

### Post by wieman01 on 2008-01-10
Mmm... Odd. Could you check my Ralink tutorial (signature) and see if you have missed anything else?

If all this does not help, we do it using a startup script.

---

### Post by Zwendel on 2008-01-11
I found it!

Thanks a lot, you were a really big help.

I had been messing around with roaming and other settings, as not to need to fire up the wireless assistant every time, and some how /etc/network/interfaces got mangled up in the process. All my references to wlan0 were gone!

So, I put those 2 lines about wlan0 back in and it works! 

The only thing that remains is the Keyring asking me for the password so that the wep key kan be accessed. Is there a way to change this? To give the network admin tool permanent access to the wep key in the keyring?

Cheers

---

### Post by wieman01 on 2008-01-11
> **Zwendel said:**
> I found it!

Thanks a lot, you were a really big help.

I had been messing around with roaming and other settings, as not to need to fire up the wireless assistant every time, and some how /etc/network/interfaces got mangled up in the process. All my references to wlan0 were gone!

So, I put those 2 lines about wlan0 back in and it works! 

The only thing that remains is the Keyring asking me for the password so that the wep key kan be accessed. Is there a way to change this? To give the network admin tool permanent access to the wep key in the keyring?

Cheers
It is possible, but since I don't use Gnome (I am on Kubuntu) you need to look around yourself. But I have seen similar posts and correponding solutions.

---

### Post by bbkid1015 on 2008-03-21
You can add the line "wireless-key your_key" to the /etc/network/interfaces file and that should make it automatic

---

### Post by kecterman on 2008-03-22
> **bbkid1015 said:**
> You can add the line "wireless-key your_key" to the /etc/network/interfaces file and that should make it automatic

I have the same problem.  That did not work for me.

---

