---
title: "Cannot browse using Ubuntu 8.10 though connected."
date: 2008-12-04
forum: New to Ubuntu
---

### Post by sadicote on 2008-12-04
When i open firefox i can connect to my ISP's client login page (which i have made my home page), put my password (ISP related), and log on. In order to browse, however, i am required to minimize that logged on window, and open a new browser window. This i could not do as firefox could not locate any other address/server. I tried "sudo aptitude update" and am attaching the screenshot of the output. This i hope, is the last obstacle to my having a fully functional Linux Desktop:)

---

### Post by falcon61102 on 2008-12-04
The errors you're getting from the aptitude update are because those addresses couldn't be reached.  If you have successfully logged on with your ISP and you cannot connect, it may be the ISP blocking you for some reason.  Is it possible that they are blocking certain OS's or firefox in general?  

Instead of minimizing the window and opening a new browser, have you tried opening a new Tab?

---

### Post by nakama85 on 2008-12-04
Just curious, Who is you provider? This info may help in the diagnoses

---

### Post by sadicote on 2008-12-04
> The errors you're getting from the aptitude update are because those addresses couldn't be reached. If you have successfully logged on with your ISP and you cannot connect, it may be the ISP blocking you for some reason. Is it possible that they are blocking certain OS's or firefox in general? 

I don't think so, because my Ubuntu is installed in Windows, and i can browse freely from there. Also, when i used firefox from my VMware guest Ubuntu, i could browse from there too. Of course, i have removed that installation(VMware based) because it couldn't detect the usb drive. So now it's a Wubi installed Ubuntu 8.10 in Windows with network connected and the restricted connectivity that i mentioned

> Instead of minimizing the window and opening a new browser, have you tried opening a new Tab?

No, the ISP people were very specific about that, the logged on Window would have to minimized and a new window opened for further browsing.:o

Tried that too, doesn't work

---

### Post by nakama85 on 2008-12-04
It really sounds like your ISP is a bad one. Any hope of switching?
I know this may not be the logical answer but if your ISP is that bad then it may be worth it in the long run.

Once again I ask who is your Internet service provider?

---

### Post by falcon61102 on 2008-12-04
It definitely sounds like an issue with Wubi relating to your ISP.  Unfortunately my experience with Wubi is very little, sorry.

And possibility of doing a dual-boot system?  That'd eliminate the problem of the Wubi conflict.

---

### Post by sadicote on 2008-12-04
If i understand correctly, Wubi is an Ubuntu installation utility, so i cannot agree that it would have any issues with my ISP, which by the way, is Net 9 Online, a channel partner/agent of Hathway Broadband services. Thank you for your suggestion. I have made a lot of people, put a lot of thought and work into this installation, to bring it to this stage, and i am not replacing it without a fight.:)

---

### Post by sadicote on 2008-12-04
I remember when editing /etc/network/interfaces as in [http://ubuntuforums.org/showthread.php?t=987012&page=2](http://ubuntuforums.org/showthread.php?t=987012&page=2), we did nothing about the DNS server addresses, preferred and alternate. Could that be a reason?

---

### Post by porchrat on 2008-12-04
> **sadicote said:**
> I remember when editing /etc/network/interfaces as in [http://ubuntuforums.org/showthread.php?t=987012&page=2](http://ubuntuforums.org/showthread.php?t=987012&page=2), we did nothing about the DNS server addresses, preferred and alternate. Could that be a reason?

Are you connecting to the internet through a router?...does the router use DHCP?

If you're connecting through a router try making the DNS your router's internal IP address (in other words the 192.168... address)

If the router uses DHCP it should be sorting all of this out for you.

Although this is all most certainly a moot point though as you can reach your ISP's homepage and therefore are connected, the only real explanation I can think of is the one everyone else has suggested already, that it is probably your ISP.

---

### Post by sadicote on 2008-12-04
It may be that my ISP has given me a connection through a router, but mine is a standalone PC and i can connect and browse from Windows, i can connect to my ISP's login page and log in, what i cannot do is open a new window or tab and connect again. Looks to me that the problem lies in configuring, either network connections, or firefox in Ubuntu; why was i able to browse using Ubuntu's firefox when installed as VMware (guest)? I had the same ISP then....

---

### Post by porchrat on 2008-12-04
Can you browse the rest of the internet?...beyond your ISP?  If your only problem is that you can't make 2 simultaneous connections to your ISP's homepage then that seems like something I could live without...it is more likely that I'm misunderstanding your problem though.

---

### Post by sadicote on 2008-12-04
In order to browse i am required to keep the logged in window open and browse from another window. I cannot connect to anything until i do that.

---

### Post by HavocXphere on 2008-12-04
Sounds like two separate problems to me. I'd suggest talking to the ISP...this business about needing to login on a page first sound like a ISP with a brain cramp policy.

As for the can't locate address: I had similar problems. Linux didn't utilize the dhcp that the router had set up. In my case "sudo dhclient eth0" helped as a bandaid solution. Then I figured out that the interfaces files had set the connection to manual configuration instead of dhcp. Replaced "manual" with "dhcp" and all is well now. Not sure whether you've got the same problem...but the symptoms sound awefully similar.

---

### Post by sadicote on 2008-12-04
Perhaps this screenshot will clarify my problem.

---

### Post by OldGrey on 2008-12-04
This is not an ISP or ISP behaviour I am familiar with. However it occurs to me, can you connect and browse if you run Ubuntu from a live CD? If so it may be something to do with the way your ISP operates and Wubi. If you can browse from a live CD it may be that dual boot would be a better option for you.

---

### Post by sadicote on 2008-12-04
No, I couldn't, and there are post's of mine where i have sought help in that regard....

---

### Post by philinux on 2008-12-04
Post the output of this command

cat /etc/hosts

---

### Post by sadicote on 2008-12-04
I have no idea why, but suddenly i am filled with hope.

---

### Post by porchrat on 2008-12-04
Generally it is easier to just copy and paste the output into your post and wrap code tags around it (that '#' symbol you see when you're typing a new post will do it).

I suppose it isn't compulsory it is just those with horrifically slow internet connections will not bother to open the images, or will take several weeks to reply while they wait for the thing to load. :D

---

### Post by sadicote on 2008-12-04
Actually, i can't copy-paste anything outside Linux, and i can only make these posts from my Windows installation. It is fortunate that i am having no problems with my pen drive (USB) detection, hence the screenshots....

---

### Post by philinux on 2008-12-04
use 

gksudo gedit /etc/hosts

delete ubuntu.ubuntu-domain

save file
reboot

---

### Post by tseligkas on 2008-12-04
Hello sadicote,

I have some remarks to make before we move on to troubleshooting:

1st. Your ISP has a very weird way of connecting you to the internet. As far as I can understand you have to logon to the gateway (192.168.19.1) to enable use of the Internet in your provider. In other words, as long as your browser keeps the session open with your gateway you are able to browse other addresses (at least when things work, e.g. in Windows).

2nd. As such, either opening a new Firefox window or a new tab in the same window you have logged on to the ISP's page should be the same.

3rd. If you use Ubuntu through wubi it shouldn't be all that different from a normal Ubuntu installation.

4th. From your post **[here]("http://ubuntuforums.org/showthread.php?t=1001510")**, we know that you use a fixed IP address. So no DHCP is used.

5th. It is likely that you can browse the internet, it's just that DNS is not set up correctly. Although you configured DNS in the Network Configuration (above link), the settings may not have been saved. (Info on DNS: Domain Name System)

How can we verify this? When I am trying to ping **[www.cnn.com]("http://www.cnn.com")** from a terminal I get the following IP address: 157.166.224.26. So, go to Firefox address field and type: **[http://157.166.224.26/](http://157.166.224.26/)** and see if you get the cnn homepage. Furthermore give us the output of your /etc/resolv.conf file.

---

### Post by sadicote on 2008-12-04
We are entirely at the mercy of ISP's here, oh yes, we have regulatory bodies like TRAI which are supposed to protect our interests, but these scoundrels and their agents can get away with blatant fraud with the help of the loopholes and lack of diligence on the part of the regulatory bodies, (I was promised a dedicated connection from the primary provider, and i wasn't told until after the wiring was done that my ISP was a channel partner/agent, my original correspondence was with the primary provider, who has washed his hands off the whole thing), but i am digressing..further to gksudo gedit /etc/hosts please find the screenshots.

The matter of configuring DNS settings..had already wondered about it in this thread, i have not configured the DNS settings yet, atleast not knowingly, and in the matter of "output of your /etc/resolv.conf file", how do i get it? I have to remind you that my knowledge of computers is very limited and more intuitive than structured,or formal and i have not yet arrived at the chapter of files and file systems in the linuxbasics.org tutorial.

My primary goal, at this moment, is to have a functional Linux Desktop, without bugs, and fully updated. I cannot even begin to learn Linux without that, can I?

---

### Post by sadicote on 2008-12-05
:D I received my Ubuntu CD and stickers from Canonical, everything went extremely smoothly--thank you, deadowl for teaching me how to properly edit the Network Settings using the GUI--even my bookmarks were imported, i use the noapic option as if it was second nature--even though i suspect i was a little messed with, i thank you all for putting me through the paces.):P

---

