---
title: "Can't set up wan miniport pppoe connection."
date: 2010-07-02
forum: New to Ubuntu
---

### Post by SKhan on 2010-07-02
My isp has recently changed its network settings. They are now using WAN miniport pppoe connection.
i asked them to setup network connection in my ubuntu installation. which they refused first but after sometime the isp person agreed to give it a try, although he had never used linux before that.
While he was trying to setup pppoe connection, he deleted the default eth0 connection. And he setup a dsl connection, only entering service , username and password. This connection never worked.
Now i am unable to connect to internet with ubuntu.
Moreover the network icon on top right of the screen has also gone, and is no more there.
i tried pppoeconf but it didn't solved the problem. What should i do now?

The only settings my isp gave me were id, password, and service name. and i successfully created a network connection in windows 7 using which i can connect to internet. The working connection reads WAN miniport pppoe.
please tell me how can i make that connection in ubuntu?

here is image of the connection that's not working in ubuntu

---

### Post by okplayer02 on 2010-07-03
Take a look here at this link the user deleted all the other interfaces except the lo or loopback interface and then used NM


[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9346744](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9346744)

hope this helps you.

---

### Post by SKhan on 2010-07-04
> **okplayer02 said:**
> Take a look here at this link the user deleted all the other interfaces except the lo or loopback interface and then used NM


[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9346744](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9346744)

hope this helps you.

ok but he didn't tell me where to enter ID, Password, and Service Name. Internet can't work without entering the service name my isp gave me.
Default eth0 connection has also been deleted by mistake, and i guess wan miniport pppoe connection won't work without an eth0 connection. because this is how it works in ms windows.
is there a way to reset network connections?

---

### Post by okplayer02 on 2010-07-04
you did not read carefully he did mention to enter your information on the dsl tab of network manager. please read carefully

---

### Post by SKhan on 2010-07-04
ok let me read once again.

---

### Post by jtarin on 2010-07-04
Do you have router? It is the simplest way to accomplish this.

---

### Post by SKhan on 2010-07-05
Just the cable is coming in my place with nothing else. I am not sure whether it's coming from a router or not. But i think they call it switch.
or 8 port switch. most of the times their brand is TP-Link.

---

### Post by jtarin on 2010-07-05
eth0 must be present for this to work.Post your results from the command ```
ifconfig -a
```then the command ```
route -n
```

---

### Post by SKhan on 2010-07-05
> **okplayer02 said:**
> Take a look here at this link the user deleted all the other interfaces except the lo or loopback interface and then used NM


[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9346744](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9346744)

hope this helps you.
this time i read it carefully and followed each step, after which the network connection icon in the top panel came back. But still i can't connect to internet.
one more question are "service" and "service name" same thing?
in MS windows we enter "service name" but in ubuntu network connect dsl tab, there no "service name" field. It's only "service" in ubuntu.

---

### Post by SKhan on 2010-07-05
> **jtarin said:**
> eth0 must be present for this to work.Post your results from the command ```
ifconfig -a
```then the command ```
route -n
```

```
khan@Khan-PC:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0d:56:be:9a:77  
          inet addr:10.117.49.5  Bcast:10.117.51.255  Mask:255.255.252.0
          inet6 addr: fe80::20d:56ff:febe:9a77/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4373 errors:1 dropped:0 overruns:0 frame:1
          TX packets:119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:10 
          RX bytes:392663 (392.6 KB)  TX bytes:11063 (11.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

khan@Khan-PC:~$ 

```
```
khan@Khan-PC:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.117.48.0     0.0.0.0         255.255.252.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.117.48.145   0.0.0.0         UG    0      0        0 eth0
khan@Khan-PC:~$ 

```

---

### Post by jtarin on 2010-07-05
> **SKhan said:**
> this time i read it carefully and followed each step, after which the network connection icon in the top panel came back. But still i can't connect to internet.
one more question are "service" and "service name" same thing?
in MS windows we enter "service name" but in ubuntu network connect dsl tab, there no "service name" field. It's only "service" in ubuntu.

Ignore "service" and "service name"......only thing you need is name and password.Your eth0 is up and running by looking at "ifconfig", it already shows an ip address.Now go to your terminal and enter  
```
sudo gedit /etc/resolv.conf
```You should have an entry(s) similar to this.```
nameserver 208.67.xxx.xxx
nameserver 208.67.xxx.xxx
nameserver 192.168.x.x
```without the x's but all numbers. These are your nameservers.You must have these to reach any address by DNS resolution.
If you do not have these you can enter the Google Public DNS IP addresses  as follows:

    ```
nameserver 8.8.8.8
nameserver 8.8.4.4
```save and try your browser.If this works we'll make it permanent.This is temporary until reboot.

---

### Post by SKhan on 2010-07-06
> **jtarin said:**
> Ignore "service" and "service name"......only thing you need is name and password.Your eth0 is up and running by looking at "ifconfig", it already shows an ip address.Now go to your terminal and enter  
```
sudo gedit /etc/resolv.conf
```You should have an entry(s) similar to this.```
nameserver 208.67.xxx.xxx
nameserver 208.67.xxx.xxx
nameserver 192.168.x.x
```without the x's but all numbers. These are your nameservers.You must have these to reach any address by DNS resolution.
If you do not have these you can enter the Google Public DNS IP addresses  as follows:

    ```
nameserver 8.8.8.8
nameserver 8.8.4.4
```save and try your browser.If this works we'll make it permanent.This is temporary until reboot.

Great tip man. I just deleted "service" and the net was working. I wonder why i never thought of deleting "service" on my own. May be because the network connection in windows 7 is not working without "service name", and because my ISP person was insisting on using service name.
However still there's one major problem. That's although i can now connect to internet via ubuntu, but the connection is unusably slow. Youtube is never fully loads up. [www.ubuntuforums.org](www.ubuntuforums.org) can't open. google search sometimes work sometimes not.

resolv.conf has only 1 name server. is it ok or do you also have a solution to make my connection as fast as it was before when my ISP needed only eth0 to work.
this connection is still working quite fast in ms windows.

---

### Post by jtarin on 2010-07-06
Add an additional nameserver. If the two I gave you don't seem to work well. Ask your ISP for nameserver addresses or Google public nameservers. Also add your gateway as a nameserver....which appears to be.....10.117.48.145

---

### Post by SKhan on 2010-07-09
> **jtarin said:**
> Add an additional nameserver. If the two I gave you don't seem to work well. Ask your ISP for nameserver addresses or Google public nameservers. Also add your gateway as a nameserver....which appears to be.....10.117.48.145

sorry my being latte. i had to reinstall ubuntu, because it had become very slow, perhaps because it was my first ever linux installation and i had messed it up.
anyways i reinstalled ubuntu 10.04. I formatted the partition before reinstallation. So it's a clean copy of ubuntu 10.04.
after installation i did nothing with the system. except for creating DSL connection. And as you told me, I ignored entering "service" field. It connected instantly, but only google.com and a few random websites worked. Other websites simply didn't load up.
i also checked google images and it too was working fast. loading images in a second or at the most 2.
but what has happened to other websites?
i checked interface file. It had only 2 lines that you told me it should have.
resolv.conf contained only 2 name servers, so i added google name servers in it, and again connected to internet. It worked in the same way as before.
then i again checked resolv.conf it was auto-edited and google name servers auto-deleted. i again tried to insert google name servers and again the same thing happened. one time during this observation, all the name servers were auto-deleted and the file was blank. but in each case google.com and google images were still working.
Then i edited dsl connection and added "service" field, and then connected to internet. It again worked in the same way.
After rebooting some hours later, i noted that the default "Auto eth0" connection has disappeared with apparantly no reason.
but google was still working.

so current state is that:
1. Default Auto eth0 connection disappeared.
2. I can still connect to internet both with and without "service" field.
3. In both the above 2 cases only google.com google images were working or a couple of random websites that appeared in search results. other websites simply didn't worked.
4. My ubuntu is clean install. With zero applications installed. No system auto-update.

Would it help you if i post output of MS windows cmd.exe "ipconfig /all" command? My ms windows connection is working perfectly.

my current terminal output for ifconfig -a and route -n are as follow:

```
sk@sk-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0d:56:be:9a:77  
          inet6 addr: fe80::20d:56ff:febe:9a77/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1497 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:10 
          RX bytes:138309 (138.3 KB)  TX bytes:1687 (1.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:139.87.48.100  P-t-P:147.233.243.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:768 (768.0 B)  TX bytes:640 (640.0 B)

sk@sk-desktop:~$ 

```
```
sk@sk-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
147.233.243.1   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ppp0
0.0.0.0         147.233.243.1   0.0.0.0         UG    0      0        0 ppp0
sk@sk-desktop:~$ 

```

---

### Post by jtarin on 2010-07-09
Edit (as root) /etc/dhcp3/dhclient.conf and find the line that reads:

```
#prepend domain-name-servers 127.0.0.1;
```

and uncomment it, and change it to:

```
prepend domain-name-servers 68.87.77.130, 68.87.72.130;
```
[COLOR="Red"](Use your nameservers)
Note the lack of the beginning hash mark, servers with an "s", a comma between addresses, and a semicolon at the end.[/COLOR]
This will make your nameservers persist each boot.

---

### Post by SKhan on 2010-07-09
@ jatarin

i followed these steps.
but still internet is working the same way.
and resolv.conf is still auto-updating.

does the following image helps you? it's from my windows7 connection that's working perfectly.
i can also post output of cmd.exe ipconfig command. if that may help you solving my problem, and if it's safe to post it here.

---

### Post by jtarin on 2010-07-09
Okay lets backup some. Try this in a terminal and post any results.
```
To connect, simply use:
sudo pon dsl-provider
To disconnect, use
sudo poff -a
```
If connected already use the command ```
sudo poff -a
```
then use the ```
sudo pon dsl-provider
```
Post an image from your Network Manager for this connection.

---

### Post by SKhan on 2010-07-10
```
sk@sk-desktop:~$ sudo pon dsl-provider
The file /etc/ppp/peers/dsl-provider does not exist. Please create it or use
a command line argument to use another file in the /etc/ppp/peers/ directory.
sk@sk-desktop:~$ 
```

Then i created the blank file "dsl-provider" in /etc/ppp/peers/ directory.

then the output was
```
sk@sk-desktop:~$ sudo pon dsl-provider
~&#65533;}#&#65533;!}!}!} }4}"}&} } } } }%}&*&#65533;},&#65533;}'}"}(}"}*}4~~&#65533;}#&#65533;!}!}!} }4}"}&} } } } }%}&*&#65533;},&#65533;}'}"}(}"}*}4~~&#65533;}#&#65533;!}!}!} }4}"}&} } } } }%}&*&#65533;},&#65533;}'}"}(}"}*}4~~&#65533;}#&#65533;!}!}!} }4}"}&} } } } }%}&*&#65533;},&#65533;}'}"}(}"}*}4~~&#65533;}#&#65533;!}!}!} }4}"}&} } } } }%}&*&#65533;},&#65533;}'}"}(}"}*}4~~&#65533;}#&#65533;!}!}!} }4}"}&} } } } }%}&*&#65533;},&#65533;}'}"}(}"}*}4~~&#65533;}#&#65533;!}!}!} }4}"}&} } } } }%}&*&#65533;},&#65533;}'}"}(}"}*}4~~&#65533;}#&#65533;!}!}!} }4}"}&} } } } }%}&*&#65533;},&#65533;}'}"}(}"}*}4~~&#65533;}#&#65533;!}!}!} }4}"}&} } } } }%}&*&#65533;},&#65533;}'}"}(}"}*}4~~&#65533;}#&#65533;!}!}!} }4}"}&} } } } }%}&*&#65533;},&#65533;}'}"}(}"}*}4~sk@sk-desktop:~$ 

```

it didn't connect to internet.

then
```
sk@sk-desktop:~$ sudo poff -a
/usr/bin/poff: No pppd is running.  None stopped.
sk@sk-desktop:~$ 

```

:( :( :(

---

### Post by jtarin on 2010-07-10
I need to see a visual of your network manager setup for this connection and a copy of your /etc/network/interfaces file

---

### Post by dineshs on 2010-07-10
SKhan,
If you want to connect using pon dsl-provider,first you should run in aterminal the command```
sudo pppoeconf
```  which will write the connection details such as username password etc in */etc/ppp/peers/dsl-provider* automatically
[COLOR="Blue"]I suggest you dont try this[/COLOR] because it will add some entry in /etc/network/interfaces also and NM wont manage your connections further.For NM to manage the connections, /etc/network/interfaces should contain only this
```
auto lo
iface lo inet loopback

```
You can configure your DSL connection via the DSL tab in Network Manager (I think you are using this now)To configure DNS,
RightClick on Network Manager icon -edit connections-click DSL tab-click the connection you have created-then edit-click ipv4 
method-Automatic PPPoE addresses only 
add DNS servers [COLOR="Blue"]4.2.2.1[/COLOR] then apply
you can try any DNS but pl check with 4.2.2.1 first
Now I think your /etc/resolv.conf will not change
If certain websites are not loading you can suspect MTU.In the DSL tab there is provision for manually setting MTU(I havent tried this)the values can be 1500,1492,1482...(trial and error)

---

### Post by SKhan on 2010-07-11
> **jtarin said:**
> I need to see a visual of your network manager setup for this connection and a copy of your /etc/network/interfaces file

here are the images.

Note: Because of this thread, i have to frequently switch between ms windows and ubuntu. So yesterday, when my mobile was connected to ms windows in pc-suite mode, I had to switch to ubuntu, but i forgot to detach my mobile, so after the start-up ubuntu instantly detected my mobile and offered a few steps to set-up mobile broadband connection. I followed all the very easy steps and the connection was setup successfully. It's in mobile-broadband tab with the name "Zong Default". It's working perfectly and all the Internet is working with this connection. Only that it costs me about quarter dollar per hour, which is expensive if converted in local currency. So i can't use mobile-broadband all the time.

---

### Post by SKhan on 2010-07-11
continued from the post above.

---

### Post by SKhan on 2010-07-11
continued from the post above...

---

### Post by SKhan on 2010-07-11
continued from the post above.

i tried to upload actual interfaces file here. but it says that file type is invalid for upload. So here is image of the actual file.

---

### Post by SKhan on 2010-07-11
> **dineshs said:**
> SKhan,
If you want to connect using pon dsl-provider,first you should run in aterminal the command```
sudo pppoeconf
```  which will write the connection details such as username password etc in */etc/ppp/peers/dsl-provider* automatically
[COLOR="Blue"]I suggest you dont try this[/COLOR] because it will add some entry in /etc/network/interfaces also and NM wont manage your connections further.For NM to manage the connections, /etc/network/interfaces should contain only this
```
auto lo
iface lo inet loopback

```
You can configure your DSL connection via the DSL tab in Network Manager (I think you are using this now)To configure DNS,
RightClick on Network Manager icon -edit connections-click DSL tab-click the connection you have created-then edit-click ipv4 
method-Automatic PPPoE addresses only 
add DNS servers [COLOR="Blue"]4.2.2.1[/COLOR] then apply
you can try any DNS but pl check with 4.2.2.1 first
Now I think your /etc/resolv.conf will not change
If certain websites are not loading you can suspect MTU.In the DSL tab there is provision for manually setting MTU(I havent tried this)the values can be 1500,1492,1482...(trial and error)

i have tried sudo pppoeconf in the start, but it didn't work for me. Now i have undone it.

---

### Post by jtarin on 2010-07-12
Have you tried setting up your eth0 in network manager wired section?
[Here's a walk-through]("https://help.ubuntu.com/community/NetworkManager0.7")

[Examples of /etc/network/interfaces]("http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/")

---

### Post by SKhan on 2010-07-12
> **jtarin said:**
> Have you tried setting up your eth0 in network manager wired section?
[Here's a walk-through]("https://help.ubuntu.com/community/NetworkManager0.7")

[Examples of /etc/network/interfaces]("http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/")

No i didn't try. I told you that default Auto-eth0 connection was disappeared after setting up dsl connection and then rebooting the system. But google was still working. Even without Auto-eth0.

Let me visit the links.

---

### Post by jtarin on 2010-07-12
Try the command ```
sudo dhclient
```this should re-enable network manager to recognize your ehternet card.

If you can still see your network icon, right click it and select Edit Connections. You should see a tab for the wired connection. Your eth0 should be listed here, highlight it then click Edit.

Check that Connect automatically has a tick in the box.

Check you have a MAC address entry.

MTU should be set to automatic

Make sure you have a tick in Available to all users

Under the IPv4 Settings, the Method should be set to Automatic (DHCP).

Click Apply, close the network connections window. Left click on the network icon, you should see Wired Network if it says disconnected click it and see if it connects, failing that do a reboot and see if that works.

---

### Post by SKhan on 2010-09-27
Sorry guys i have been out of city for 2 months. But now i am back. I will re-read this thread, then continue the topic in a couple of days from where it was left.
In-short the problem is still not solved.

---

### Post by jtarin on 2010-09-27
We're ready to get to work when you are.

---

### Post by SKhan on 2010-10-19
there's one problem. Having forgotten a lot during this time, I am at a loss to know where to start it again. I have a feeling that everything's been messed up. Thinking about clean install again.
I couldn't use linux for 3 months and i really have forgotten a lot. I already was a new user. I have once again become a new user. :(

---

### Post by jtarin on 2010-10-19
That's good! I would suggest a reinstall now that you know a little more and suggest making a new post titled "PPOE Connection Help", so we can start fresh. Do not try to setup any connection until you post and we can help from the beginning. Make sure in your post you mention about what hardware you are using to make your connection. You might make a link to your new post from this one in case someone searches and reaches here. This way they can continue there search.

---

### Post by SKhan on 2010-10-20
> **jtarin said:**
> That's good! I would suggest a reinstall now that you know a little more and suggest making a new post titled "PPOE Connection Help", so we can start fresh. Do not try to setup any connection until you post and we can help from the beginning. Make sure in your post you mention about what hardware you are using to make your connection. You might make a link to your new post from this one in case someone searches and reaches here. This way they can continue there search.

Thanks jtarin. Let me proceed with the reinstall. :)

---

### Post by SKhan on 2011-11-05
This problem is solved a couple of days ago. It took me 16 months to solve this problem.
I installed fresh copy of Ubuntu 11.10, added the DSL connection, just entered username, service & password and the system  was connected to internet with full speed.
On the other hand the same steps were of no use with fresh installation of previous versions of Ubuntu.
The difference is that 'Allow Deflate Data Compression' is by default checked in 11.04 while unchecked in previous ubuntu versions.
Send 'PPP echo packets' is by default unchecked in 11.04 whiled checked in previous ubuntu versions.

In case it helps someone, i am posting successful settings.
[IMG]http://img253.imageshack.us/img253/2748/96540341.png[/IMG]
[IMG]http://img259.imageshack.us/img259/8848/61038242.png[/IMG]
[IMG]http://img835.imageshack.us/img835/4996/80814287.png[/IMG]
[IMG]http://img217.imageshack.us/img217/2843/65552227.png[/IMG]

---

