---
title: "How can I install libgnomevfs2-extra with no internet?"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by piergen on 2011-01-12
I need to get **libgnomevfs2-extra** in order for nautilus and gnome commander to see the samba share. Apperantly ```
sudo apt-get install libgnomevfs2-extra
``` would easily solved my problems.

But I dont have dsl connection at the moment. How can I install them manually?

I do however have a windows laptop connected to the network. Laptop connects to internet via smart phone but I cant seem to be able to share that connection correctly.

What to do?

---

### Post by Soulcage on 2011-01-12
[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")
You may run into dependancy hell though.

---

### Post by piergen on 2011-01-12
Thx, but now I am totally confused because there where lots of depandancies. 
Question is though will I only need to install the list 9 dependancies listed in embedded jpg? 
Or as I click each and every of them 9 files I can see even more dependancies. What I mean is that when I am on the [download site for libgnomevfs2-extra. ]("http://packages.ubuntu.com/hardy/libgnomevfs2-extra")
I can now see there are a totalt of 9 depends listed. Ok so if I need 10 files total I am fine. That is doable even via slow mobile connection to internet.

But if I click on each and all of the 9 files I can see that for all of them there are even more depends. If we add up all them new depends too thats make for a total of 50 depends. And not even counting recomends or suggest.


Will I only need to install the first [9 depends listed here?]("http://packages.ubuntu.com/hardy/libgnomevfs2-extra") or all files linked to by the 9 depends too?

How does one make sure any future updates of manual installs are done? I mean as long as install is not done by terminal or packetmanager one must manage updates manually?

---

### Post by piergen on 2011-01-12
Hmm. Does not seems people are sure here.
Only other option would be to be able to share the internet connection from my win XP laptop to my xubuntu box. The thing is I am connected to home network via a netgear switch. The switch act as DHCP and delivers IP adresses to all computers on network also the win xp when I have that one connected. When I click on properties for local area connection for the wondows mobile I know I can share internett connection if I mark that in the advanced tab. Thin is when I try to share internett connection I get this error:

> 
A LAN connection is already configured
with the IP address that is required for automatic IP addressing[Googling that error message  ]("http://www.google.com/search?client=firefox-a&rls=org.mozilla%3Anb-NO%3Aofficial&channel=s&hl=en&source=hp&q=A+LAN+connection+is+already+configured+with+the+IP+address+that+is+required+for+automatic+IP+addressing&btnG=Google+Search")I learn this:

>  **Explanation:** 
 Internet connection sharing configures  the LAN connection of the home network or small office network with a  static address. There is another network adapter in the system that is  configured with the same address.
  **User Action:** 
  Change the static address of the network adapter before enabling Internet connection sharing.

I also see this:
> To use ICS, change the wired network to a different address range,
such as 192.168.1.x.

That mask simply means that IP
addresses that are the same in the first three numbers are in the same
subnet.  For example:

192.168.0.1 and 192.168.0.10 are in the same subnet
192.168.0.1 and 192.168.1.1 are in different subnets

And how can I assign different subnet when all IP's are given from the netgear switch?
Do I need crossed cables and direct pc to pc connection to fix this? Or is there maybe a smart trick that might help?

---

### Post by piergen on 2011-01-12
Pls a little help here. I have a quota on the windows mobile I currently uses to wonnect windows pc to internet, so I would really not like to start this without knowing if there is total of 10 downloads or 50 downloads. If I use over qouta that breaks the bank and I get huge fine in form of big bill. 

So what do you think, will it be only the 9 depends listed on the page I linked into earlier?

---

### Post by piergen on 2011-01-12
What a drag to be off the grid.
After first install I could not go further because I got error:

[B]
Broken dependecies[/B] 
Your system has broken dependencies. This application can not continue untis this is fixed. To fix it run "sudo synaptic" or "sudo apt-get install -f" in a terminal window.

If I do choose to download all 50 files how can I manually go around the error messages? Cause as it stands I can not dbl click any of the deb files before dependencies are fixed.

---

