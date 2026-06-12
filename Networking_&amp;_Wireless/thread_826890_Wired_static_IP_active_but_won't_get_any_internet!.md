---
title: "Wired static IP active but won't get any internet! HEEELP!"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by oleksus on 2008-06-12
I had my Ubuntu (Hardy) laptop connected via DHCP at work, nice and easy.

Now I'm using it at home, where I have only **static IP** (which works well under weendoves).

Everything seems OK, IP and DNS set, **wicd** sees my connection, says 'connected IP blah blah'...
[COLOR="DarkRed"]BUT I CAN'T GET NO INTERNET![/COLOR]
[B]
I can see packages sent and received![/B] But still cant go to any website!

The *sudo lshw -C network* shows this (posting only part):

```

description: Ethernet interface
vendor: Intel Corporation
physical id: a
logical name: eth0
......

```

**What on earth am I possibly missing here?**

**PS:** I can see there is a **'workgroup'** specified among my provider's specs on a paper. Should I maybe enter it somewhere?

---

### Post by superprash2003 on 2008-06-12
try pinging your router and post output.. also try ping google.com and post output

---

### Post by michelnacouzi on 2008-06-12
I installed the package of sc92031.c however, after i restart the computer, the computer does not see any ethernet driver, i have to reinstall it. And when i install it, the computer cannot automatically obtain an ip address and if I use the static ip address the same as the one obtained in Windows XP, the internet does not work. I search a lot, and all the commands I used didn't work. Plz any help???

---

### Post by Mako Eyes on 2008-06-12
If your computer says it's connected but it can't get anywhere then it sounds to me like there's a problem with your DNS server addresses. To find out what DNS (Domain Name System) addresses you should use, try Googling to see what ones are available through your ISP (Google: DNS address <name of ISP>, for example) or you can call your ISP and ask them, they should know it.

Mind you, that all worked well for me in Windows, but I too am having trouble setting up a static IP address in Ubuntu. If you're interested, I have a thread about it [here](http://ubuntuforums.org/showthread.php?t=826987).

---

### Post by linux6994 on 2008-06-12
Sounds like the DNS and GW IP are not set. When you set the static IP ie.. 192.168.1.11 you should set your DNS and GW IP to the IP address of your router. When running DHCP this happens automatically.

---

### Post by Mako Eyes on 2008-06-12
> **linux6994 said:**
> Sounds like the DNS and GW IP are not set. When you set the static IP ie.. 192.168.1.11 you should set your DNS and GW IP to the IP address of your router. When running DHCP this happens automatically.

By "GW IP" do you mean the Gateway Address? If so then this advice does not work for me. I tried setting the DNS address to the same IP as my router and also to the DNS addresses supplied by my ISP. None of these work for me in Ubuntu.

---

### Post by oleksus on 2008-06-12
> **superprash2003 said:**
> try pinging your router and post output.. also try ping google.com and post output

I tried *'ping [http://www.ubuntu.com](http://www.ubuntu.com)'* as well as some other addresses, but get the same response: '*ping: unknown host *...."
By the way, _how to ping my router_? 

> **linux6994 said:**
> Sounds like the DNS and GW IP are not set.
Everything is set properly, triple checked: IP, GW IP, netmask, static DNS + secondary + tertiary DNS.

BUT, there is still this 'workgroup' option mentioned on my provider's plastic card. It's like that 'mshome' network name in MS Weendows which should absolutely be set in some local networks. 
I wonder if THIS could be the problem?

---

### Post by superprash2003 on 2008-06-12
open firefox and type [http://64.233.187.99](http://64.233.187.99) does google page open?

---

### Post by oleksus on 2008-06-13
Nope, nothing opens. It obviously cannot connect to anything, but wicd shows that the network is active.
Frustrating.

---

### Post by Mako Eyes on 2008-06-13
I found out my problem, and hopefully yours will be solved too. I noticed that changing my Internet connection settings for a static IP would automatically refresh the connection, but setting up DNS addresses would *not*.

So, I thought to myself what would happen if I refreshed the connection *after* I put in my custom DNS addresses and lo and behold, I now have a static IP. It was pretty neglectful of me to not even try that before.

So, I say to you, **change your DNS addresses first**. After that you can then try changing your IP, Subnet Mask, and Gateway addresses so that the connection refreshes itself with these new DNS addresses.

Hope that helps!

EDIT: That said (and I know it's a bit off-topic, but it's not worth opening a new thread), how do I get rid of the network icon in the notification area? I usually prefer that space be used by applications that I'm using and having that icon there all the time kind of clutters it and it's a little irritating.

---

### Post by superprash2003 on 2008-06-13
i dont think its a DNS Problem because you are not able to access google's site by its ip address

---

### Post by issih on 2008-06-13
You can remove the network manager applet by going to System->Preferences->Sessions and then unticking the Network Manager in the Current Session list.

It won't then start on next boot. To kill it right here and now, just close the process nm-applet.

Quick note to say you should definitely set up two locations in the network dialog, as then you can just use that to switch profiles between work and home.

---

### Post by Mako Eyes on 2008-06-13
> **issih said:**
> You can remove the network manager applet by going to System->Preferences->Sessions and then unticking the Network Manager in the Current Session list.

It won't then start on next boot. To kill it right here and now, just close the process nm-applet.

Okey dokey, that worked. Thanks.

---

### Post by oleksus on 2008-06-13
Nothing works for me, DARN!

My guess now is that the problem is either in **IPv6** (which is not supported by my provider) and I don't know how to switch it off,
or that stoopid **'workgroup'** which is not set somewhere.

BUMP :(:confused:

---

### Post by michelnacouzi on 2008-06-14
Thank you very much, I added the DNS server first, and then i set a static ip, and the connection worked. I still have a problem however. I had this problem before, and it still persist. After working about 6 hours, (because i'm new in linux) i was able to generate an sc92031.ko file and i put it in .../drivers/net/, then, according to the instructions, i wrote 'insmod sc92031.ko' on the terminal, and then the computer recognized the ethernet card. however, every time i reboot my computer, the eth0 is not recognized, i have to go again to the terminal and write insmod sc92031.ko, Is there any way that i can tell my computer to do this automatically.
In the readme file they told me to make sure that the line : 'alias eth0 sc92031' is found in /etc/modules.conf. On my computer i have /etc/modules without an extension, i didn't find this line so i added it, and it didn't work. Then i tried putting only 'sc92031', and it didn't work as well. Any sugeggestions please?

---

### Post by Mako Eyes on 2008-06-14
> **michelnacouzi said:**
> Thank you very much, I added the DNS server first, and then i set a static ip, and the connection worked. 

Glad I could help. As for your other problem, I'm afraid I have no idea how to assist you on it.

---

