---
title: "Ubuntu to Ubuntu Network Sharing"
date: 2015-10-08
forum: Networking &amp; Wireless
---

### Post by roten-ben on 2015-10-08
Hi guys, I have ssh (SFTP I guess?) setup between my two Ubuntu desktops. For ease of explanation, my first desktop is computer A and the second is B. My problem:

I can connect to computer B from computer A using the saved sftp command (under Connect to Server in file browser) specifying it's hostname and user login. It works every time. I used to be able to do the same from computer B to computer A. I updated the hostname of computer A by editing the /etc/hosts and the /etc/hostname files properly. Afterwards, the connection from B to A using A's hostname only worked part of the time (just times out). Now it never works and I am only able to connect to A from B if I manually look up A's IP address. Obviously this is pretty annoying. How can I fix this? Thanks!

---

### Post by howefield on 2015-10-08
You could set the machine a static IP address ?

---

### Post by Morbius1 on 2015-10-08
All Linux, OSX, and now Win10 machines can use a ".local" domain qualifier on their host names to connect within a LAN so you might want to try that.

Instead of specifying MachineA use MachineA.local

The only requirement is that avahi-daemon is running and it's port ( 5353 ) is open.

---

### Post by roten-ben on 2015-10-08
Avahi-daemon did not work, I'll try setting a static IP. If anyone else has any ideas how to get the original hostname method working let me know!

---

### Post by Morbius1 on 2015-10-08
> Avahi-daemon did not work
I don't know what that means.

You checked to see if avahi-daemon is running on both machines:
```
sudo service avahi-daemon status
```
And if they weren't stated it:
```
sudo service avahi-daemon start
```
Made sure that at least it's port was open at 5353 as well as the ssh port of course..

And it wouldn't connect?

---

