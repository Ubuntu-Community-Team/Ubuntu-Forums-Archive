---
title: "Newbie: Static IP=Greek to me"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by khardbored on 2007-05-30
Ok, before I start this novella I will explain my current configuration.

I'm using an Actiontec GT701 modem from qwest. This modem is then connected to a 5-port switch. Which then feeds 4 computers and an Xbox 360. Everything works great. Everyone has internet access, including me and my Ubby machine. The problem begins when I try to setup some port forwarding for my torrent client. The last number will randomly change, in my IP. So, I am told that I need to set up some port forwarding for this computer. Sounds great. I can do that....ok, I can't do that. It's all freaking greek to me. Networking stuff just makes me feel like the most idiotic guy ever to disgrace Linux with his use. So yeah, I really don't knowmuch aobut how to start doing this.

I know that my modems configuration page is at 192.168.0.1 and has all sorts of spiffy options. I also know that I would like this computers ip to be say, 192.168.0.100 but yeah, I've tried doing it numerous times and it just doesnt want to work. Any help will be greatly appreciated and will make a newbie feel like he is actually getting somewhere in this big, scary Linux world!

---

### Post by ellisdee on 2007-05-30
To setup a static IP address for your PC you need to -
Edit /etc/network/interfaces with your favourite text editor as root

Here's how I would go about doing it

From a terminal -
shan@schlappy:~$ sudo vi /etc/network/interfaces

Probably looks something like -

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

You need to change it to look like this -

iface eth0 inet static
       address 192.168.0.100
       netmask 255.255.255.0
       gateway 192.168.0.1

You will then need to restart networking like this -
shan@schlappy:~$ sudo /etc/init.d/networking restart

You will then need to add your DNS servers by editing /etc/resolv.conf -
shan@schlappy:~$ sudo vi /etc/resolv.conf

to look like this -
nameserver 192.168.0.100

or add your DNS servers that are supplied by your ISP.

So you have now set a static IP address for your PC you will then need to add port forwarding on your modem/router (you may need consult your modem manual on how to do so)

Example would be your torrent client uses port 123456 you would need to go to your modems setup page as you said [http://192.168.0.1/](http://192.168.0.1/) and port forward port 123456 to 192.168.0.100

Hope this helps ;)

---

### Post by khardbored on 2007-05-30
I've done all that before and it didn't work. When I login to my modems admin page and view active users, im still listed as one of the usuall IP's.

I just don't understand why it won't take...

---

### Post by sysdrum on 2007-05-30
You need to set the ip out of the DHCP (Dynamic Host Configuration Protocol) Range
It sounds like 100 is still in the range so it is just ignoring the static request and is giving you a DHCP ip address. 

This should give you more info then I could ever explain
[http://www.yolinux.com/TUTORIALS/LinuxTutorialNetworking.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialNetworking.html)

DHCP
[http://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol](http://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol)


hope this helps

---

### Post by khardbored on 2007-05-30
Thanks for the links, good overall information. I tried some of the things listed there and to no avail. I tried setting my IP out of range and nothing...I believe I tried 192.168.10.1 and this time I didn't have any internet access...

This really is starting to suck :(

---

