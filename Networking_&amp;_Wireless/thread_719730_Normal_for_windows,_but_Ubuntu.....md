---
title: "Normal for windows, but Ubuntu....?"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by allanco on 2008-03-09
I've gone through 14 pages on this particular section and despite seeing similar questions I have yet to see the answer.
The question is; when I boot up a windows pc I am instantly connected to the internet, I don't have to do a thing, Windows has kept the details of my SSID and security key and I am connected.
In Ubunto I have to find my SSID in the network manager and key in my key every time I boot.
Is there a way for Ubuntu to remember my details so that I'm connected from the moment I see the desktop?

If there is an answer can it be in noobie speak as I am new to the command line!

Cheers

---

### Post by Eiríkr on 2008-03-09
> **allanco said:**
> I've gone through 14 pages on this particular section and despite seeing similar questions I have yet to see the answer.
The question is; when I boot up a windows pc I am instantly connected to the internet, I don't have to do a thing, Windows has kept the details of my SSID and security key and I am connected.
In Ubunto I have to find my SSID in the network manager and key in my key every time I boot.
Is there a way for Ubuntu to remember my details so that I'm connected from the moment I see the desktop?

If there is an answer can it be in noobie speak as I am new to the command line!

Cheers

Have a look at the sticky post [here]("http://ubuntuforums.org/showthread.php?t=684495"), it's listed right at the top of the page.  Network Manager is sadly a buggy and feature-sparse program that will hopefully be either fixed or replaced in the next Ubuntu release.  

Cheers,

Eiríkr

---

### Post by TheWizzard on 2008-03-09
> **Eiríkr said:**
> Have a look at the sticky post [here]("http://ubuntuforums.org/showthread.php?t=684495"), it's listed right at the top of the page.  Network Manager is sadly a buggy and feature-sparse program that will hopefully be either fixed or replaced in the next Ubuntu release.  

Cheers,

Eiríkr

his network works already. so all this stuff with network manager is not necessary.

just do the following:
open terminal and type:
```
sudo nano -B /etc/network/interfaces
```

then go to the interface that is used to connect to the internet and add the wireless-essid and wireless-key. like this: 

auto eth1
iface eth1 inet dhcp
wireless-essid [the name of your network]
wireless-key [your key]

---

### Post by allanco on 2008-03-10
I had a go at Thewizards suggestion, but it didn't work.
I found that the wireless connection was saved okay and the wireless notification area changed from the blue stepped signal icon to a one screen on top of the other icon.
I am a linux noobie so maybe I got something wrong when using the terminal.

when I first opened up the interfaces dialogue I had this already in place:

auto lo
iface lo inet loopback

so i deleted that and then put in the following

auto wlan1
iface wlan1 inet dhcp
wireless-essid joebloggsdsl
wireless-key 1234abcd

Then I hit ctrl x to exit
 Save modified buffer? was asked and I clicked yes, and then "filename to write" was asked, hitting return seemed to save it, as when I re input the command  "sudo nano -B /etc/network/interfaces" it had all changed to what I put in.
However on restarting the pc there was no wireless connection, so I am still confused:(

---

### Post by Eiríkr on 2008-03-10
Unfortunately, the "lo" lines are needed for what's called the "loopback" interface, which is a way for a machine to contact itself via the networking stack.  Network Manager has a reputation of overwriting the contents of the file in some circumstances, so it's possible those lines have automatically been added back.  If they have, though, chances are that the wireless config lines you added are no longer there.  Go back into the /etc/network/interfaces file and let us know what you find.

---

### Post by allanco on 2008-03-10
Because I couldn't get connected to the net at all, I changed back to the way it was when I started, so it currently reads:

auto lo
iface lo inet loopback


So do I need those lines in there and add the others to it?

---

### Post by Eiríkr on 2008-03-10
Exactly.  Then, to be sure, try rebooting and checking to make sure it still works.  If not, check the contents of the /etc/network/interfaces file, and if it's different from when you last edited it, then it's being overwritten by some process during boot.  Let us know what you find.

---

### Post by allanco on 2008-03-10
Many thanks for your help Eiríkr, it's nearly midnight here, so i'm off to bed but will try again tomorrow!
Cheers
Allan

---

### Post by allanco on 2008-03-11
Nearly but not quite!
The interface changes its contents slightly:

What I first put in:

auto lo
iface lo inet loopback
auto wlan1
iface wlan1 inet dhcp
wireless-essid joebloggsdsl
wireless-key 1234abcd

This then changes to the following:

auto lo
iface lo inet loopback
auto wlan1
iface wlan1 inet dhcp
wireless-key S: 1234abcd
wireless-essid joebloggsdsl


The wireless key and ssid parts get swapped around and an extra s and colon are added.
When I check the properties of the wlan1 I notice that the key is using hexidecimal encrytion so I have to change it to ascii, this is when the above change takes place in the interface.
I can then connect to the internet, until I reboot.
Everything is exactly the same, in order to get a connection I have to delete the extra s and colon and swap the lines around and change the key in properties to ascii again, but that will only work until I reboot as the line changes again. 
Hope this makes sense.

---

### Post by Eiríkr on 2008-03-11
Hey there Allan --

That's a puzzling set of symptoms there.  I don't have wireless on any of my Ubuntu machines, so I'm afraid I can only pass along what I've read rather than any first-hand experience.  That said, let me suggest one easy-ish possibility here, which is to effectively lock your interfaces file to prevent anything from changing it, by running the following:
```
sudo chattr +i /etc/network/intefaces
```
The "+i" bit adds the "immutable" attribute to the file, rendering it inalterable and undeletable.  Do this *after* making any needed changes, then reboot and make sure everything still works.  Also note that you will have to *remove* the immutable attribute should you ever need to make additional changes, like this:
```
sudo chattr -i /etc/network/interfaces
```
I'd strongly recommend printing this out or writing it down somewhere, so that if your network *doesn't* work after reboot, you still have the instructions in front of you for how to undo the immutability.  :)  

This is admittedly a bit of a cludge, but it's a quick-and-dirty fix that is at least nice and easy.  

HTH,

Eiríkr

---

### Post by allanco on 2008-03-11
I gave that a go, it stopped the details in the interface from changing but the wireless properties insisted on a hex key, so no amount of changing the file and typing and retyping would work.
I guess I'll have to stick with putting the key in each time manually (even tried the keyring manager and that doesn't work).

Many thanks for all of your suggestions and advice, at least it helped get me a bit more familar with the command line.:)

---

### Post by Eiríkr on 2008-03-11
Glad to hear we've been able to help a bit, then.  And welcome to the CLI side of things!  :D

Cheers,

Eiríkr

---

### Post by Eiríkr on 2008-03-11
> **allanco said:**
> Nearly but not quite!
The interface changes its contents slightly:

What I first put in:

auto lo
iface lo inet loopback
auto wlan1
iface wlan1 inet dhcp
wireless-essid joebloggsdsl
wireless-key 1234abcd

This then changes to the following:

auto lo
iface lo inet loopback
auto wlan1
iface wlan1 inet dhcp
wireless-key _**S:**_ 1234abcd
wireless-essid joebloggsdsl


The wireless key and ssid parts get swapped around and an extra s and colon are added.
When I check the properties of the wlan1 I notice that the key is using hexidecimal encrytion so I have to change it to ascii, this is when the above change takes place in the interface.
I can then connect to the internet, until I reboot.
Everything is exactly the same, in order to get a connection I have to delete the extra s and colon and swap the lines around and change the key in properties to ascii again, but that will only work until I reboot as the line changes again. 
Hope this makes sense.

I found in the [FONT="Courier New"]iwconfig[/FONT] man page that the **_S:_** bit is required for ASCII keys:
> **key/enc[ryption]**

Used to manipulate encryption or scrambling keys and security mode.  To set the current encryption key, just enter the key in hex digits  as  _XXXX-XXXX-XXXX-XXXX_  or _XXXXXXXX_.  To set a key other than the current key, prepend or append [index] to the key itself (this won’t change which is the active key). **You can also enter  the  key  as an ASCII string by using the s: prefix**. Passphrase is currently not supported.

< ... snip ... >

Examples :

```
iwconfig eth0 key 0123-4567-89
iwconfig eth0 key [3] 0123-4567-89
**iwconfig eth0 key s:password**
```

Judging from the example here, there should be no space between the **s:** and the key value.

HTH,

Eiríkr

---

### Post by allanco on 2008-03-11
I'll give it one more go and post back tomorrow.
I really appreciate all your help Eiríkr,your a star!:KS

---

### Post by allanco on 2008-03-14
Still no joy in the end, tried to give everything a go, but something is causing a conflict somewhere.
So unless there is anything else to try (any other data that is being held elsewhere?) then I'll have to stick to typing in my essid and password each time
Thanks again for all help offered

---

