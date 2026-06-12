---
title: "Wireless connection doesn't work..."
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by Cr00zng on 2007-03-05
New at Ubuntu and/or Linux in general; just some minimal knowledge with other distros. Here's my experience with the wireless setup for Ubuntu.

Dell 620 laptop with IntelPro 3945 Wi-Fi card running Ubuntu 6.10; the card is detected during installation and the appropriate driver is installed. It cannot connect to my Juniper wireless broadband router; the router has this error message in the log:

======================================
Wireless station event: Station 0018dexxxxxx Authentication type not accepted, Type: OPEN, SSID: xxxxxxxx.
======================================

Simple enough, let's change the "Type:" in Ubuntu to "SHARED" which is how the router is configured. Just go to "\System\Administration\Network" and huh? There's no such setting under the "Wireless connection".

That's kind of retarded to assume by the installation routine that a broadband router with security enabled it'll be the open type, but whatever. Let's use some CLI tools such as iwconfig to set the type correctly, huh? The CLI tool has no provision for changing the authentication type, but whatever.

Break out gedit and change the file "/etc/network/interfaces" and replace the line of:

wireless_keymode open

to

wireless_keymode shared

Well, gedit won't do it since I am not logged in as root; simple enough, just logon as root. 

What the @#$%, what do you mean that the root cannot logon locally on this laptop? Are you out of your @#$% mind? Oh well, let's log back as standard user, and type in:

sudo vi /etc/network/interfaces

Here we go, now it's fine; just add the line listed above save it and we are ready to browse the web. Not so fast, maybe my limited knowledge with vi messed up this file; the wireless connection doesn't try to connect now. On the flip side the constant trying of the authentication by Ubuntu to my broadband router acted as a "DoS" since I've also got the following error message in the log:

===========================================
Session utilization has reached 1857, which is 90% of the system capacity!
===========================================

No wonder my Internet connection became slow on my other machine.

So, at the moment the wireless connection is disabled. Does anyone know how to make Ubuntu to use shared authentication type instead of the open type? I am pretty sure it is not that hard, but it looks different from my seat.
10QIA...

Cr00zng

---

### Post by Cr00zng on 2007-03-06
> **Cr00zng said:**
> New at Ubuntu and/or Linux in general; just some minimal knowledge with other distros. Here's my experience with the wireless setup for Ubuntu.

Dell 620 laptop with IntelPro 3945 Wi-Fi card running Ubuntu 6.10; the card is detected during installation and the appropriate driver is installed. It cannot connect to my Juniper wireless broadband router; the router has this error message in the log:

======================================
Wireless station event: Station 0018dexxxxxx Authentication type not accepted, Type: OPEN, SSID: xxxxxxxx.
======================================

Simple enough, let's change the "Type:" in Ubuntu to "SHARED" which is how the router is configured. Just go to "\System\Administration\Network" and huh? There's no such setting under the "Wireless connection".

That's kind of retarded to assume by the installation routine that a broadband router with security enabled it'll be the open type, but whatever. Let's use some CLI tools such as iwconfig to set the type correctly, huh? The CLI tool has no provision for changing the authentication type, but whatever.

Break out gedit and change the file "/etc/network/interfaces" and replace the line of:

wireless_keymode open

to

wireless_keymode shared

Well, gedit won't do it since I am not logged in as root; simple enough, just logon as root. 

What the @#$%, what do you mean that the root cannot logon locally on this laptop? Are you out of your @#$% mind? Oh well, let's log back as standard user, and type in:

sudo vi /etc/network/interfaces

Here we go, now it's fine; just add the line listed above save it and we are ready to browse the web. Not so fast, maybe my limited knowledge with vi messed up this file; the wireless connection doesn't try to connect now. On the flip side the constant trying of the authentication by Ubuntu to my broadband router acted as a "DoS" since I've also got the following error message in the log:

===========================================
Session utilization has reached 1857, which is 90% of the system capacity!
===========================================

No wonder my Internet connection became slow on my other machine.

So, at the moment the wireless connection is disabled. Does anyone know how to make Ubuntu to use shared authentication type instead of the open type? I am pretty sure it is not that hard, but it looks different from my seat.
10QIA...

Cr00zng

Well, I was on the right track with the wrong syntax; here's the correct one that I've found on the web:

wireless_keymode restriced

I just wish that this information is more readily available; better yet the GUI should have a provision for changing the keymode. After all this is rather common setting with broadband wireless routers with WEP enabled; having the same terminology within Ubuntu as the broadband routers have would actually make sense.

Cr00zng

---

