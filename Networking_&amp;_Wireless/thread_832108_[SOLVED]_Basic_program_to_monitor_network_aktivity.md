---
title: "[SOLVED] Basic program to monitor network aktivity?"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by hovzio on 2008-06-17
Hello,

      I have a few "noob" questions concerning the viewing of my network aktivity, please bare with me :)

      I use firestarter as a firewall and from it I am able to see all aktive connections, blocked connection, data transfer etc. On several occasions I've found it usefull to access these *infos but I must say using a firewall for this purpose is rather tedious since I actually  rarely need to edit it and above all I need root privileges to access firestarter. Most of the time I am working with a regular acount not in the admins group so from there I cannot access firestarter. (could edit sudoers but somthing tells me there are alternatives to a firewall to view these *infos.)

     So..to my question. Is there a program that lets me view open connections and transfer rate?
     I'm not looking for some program that puts my nic in promiscuous mode, monitors packets, i.e. wireshark. A command line application would be great for I could just open a virtual console and if need be run as root, but a gui is fine. Thanks for any input.

---

### Post by fain on 2008-06-17
netstat will give you active connections but not transfer rates i don't think. Check "man netstat" for more info.

---

### Post by hovzio on 2008-06-17
Thanks, sounds good. I'll check it out.

---

### Post by PadreSol on 2008-06-25
netstat is fine depending on what you want to do. Also look in 

 /proc/net/socket
 /proc/net/dev
 /proc/net/if_inet6

Also I just discovered, to my dismay, that ubuntu is using a very old netstat from 2001.

---

### Post by hovzio on 2008-06-26
@ PadreSol: hi, thanks for the reply. I viewed  the files with cat and got some useful information.There is no such file in my system: /proc/net/socket. The other two exist and there were a number of other interesting files in /proc/net/. The whole proc directory seems altogether rather interesting.

You are right about netstat, it kicks out a lot of info:confused:  There has to be a simple little program that just lists my current connections in "human readable" output. (I'm no dns server and sure I can use host to figure it out but..). Now what would be really cool would be if you could log all the traffic. The info you provided is neat and will help further my knowledge concerning GNU/linux but its not quite what I'm looking for. Nevertheless thanks

---

### Post by PadreSol on 2008-06-26
Also have a look at lsof, it's an amazing tool.  The /proc filesystem is chocked full of goodness.  I urge to to check it out.  Although I think it's being replaced.

---

### Post by lemuriaX on 2008-06-26
Some great info here, but like hovzio I would also love to have a GUI I could use to monitor port activity on the fly...much like firestarter does but without having to run Firestarter since it's really a GUI for managing IPTables and runs as root.

Anyone have any ideas?

---

### Post by sefs on 2008-08-01
Have any of you found that gui program that does what firestarter does in relation to Active Connections.  I would love a program like this.

P.S.  with the source from firestarter available @ [http://www.fs-security.com/download.php](http://www.fs-security.com/download.php), how daunting a task is it to strip out just the part that gives the active connections and and make a simple applicaton that just does that.

---

### Post by hovzio on 2008-08-02
> **sefs said:**
> Have any of you found that gui program that does what firestarter does in relation to Active Connections.  I would love a program like this.

P.S.  with the source from firestarter available @ [http://www.fs-security.com/download.php](http://www.fs-security.com/download.php), how daunting a task is it to strip out just the part that gives the active connections and and make a simple application that just does that.

hi, I still haven't been able to find anything. I find netstat to be alright although it doesn't (or I havent figured it out..) show the amount of traffic. I think that it would take quite a bit of effort to appropriatley modify firestarter although I am not sure of this. One thing I have thought of is something along the lines of screenlets or gdesklets. A little python script could possibly do the trick. I have one that reports on the amount of traffic being used by various devices. Just an idea, I wouldn't be able to write this little gadget but I think it may be a proper alternative to modifying firestarter. Will reply if I do happen to stumble upon something :popcorn:

---

### Post by tact on 2008-08-02
Does Etherape give what you want? GUI.  Shows  all connections.  Click to see packet throughput data.  Colours indicate protocol.  thickness of line indicates bandwidth.

---

### Post by sullenx on 2008-08-04
Etherape is a very cool tool!...Best of its kind!!! Thanks for posting it!:popcorn:

---

### Post by hovzio on 2008-08-04
> **tact said:**
> Does Etherape give what you want? GUI.  Shows  all connections.  Click to see packet throughput data.  Colours indicate protocol.  thickness of line indicates bandwidth.


Best that I have found so far. Kinda neat. Thank you!  :)

---

### Post by hovzio on 2008-11-09
Hi, I have finally found a pretty cool prog., its called iftop. Its in the repos and a pretty strait forward konsole app. You do have to run it with root privledges but I suppose there's now way around that one. After installation you run it with:


sudo iftop -i [specify an interface, ath0, eth0 ra0...]


:)

---

