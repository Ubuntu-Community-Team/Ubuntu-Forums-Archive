---
title: "Cannot see shared folders from XP network!"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by cyclingman on 2008-01-01
I am on a wireless network with other windows XP users, I am using Gusty Ubuntu and am trying the see their shared folders. If I go to Places > Network, I can click on "Windows Network" and then "mshome".

But then I get the following message:

[SIZE="4"]"The folder contents could not be displayed."[/SIZE]
"Sorry, couldn't display all the contents of "Windows Network: mshome""

Then none of the shared folders that I can see from other computers appear. Why? What does this mean? Help please ,-)

---

### Post by Predator[23rd] on 2008-01-01
firewall???

are your 445 and 139 TCP ports open?

---

### Post by cyclingman on 2008-01-01
Forgot to say; Im a begginer. How can I check please?

---

### Post by RxRated on 2008-01-03
I'm having the same issues.  I made sure my firewall (zonealarm) was turned off on my winxp machine but still had same problem.  I CAN access my ubuntu shared folders from my winxp computer.  I really want to get this working so my network printer(on the winxp computer) will work for me.

---

### Post by cyclingman on 2008-01-04
Did you (or anyone) find a solution?:(

---

### Post by Al42 on 2008-01-04
> **RxRated said:**
> I'm having the same issues.  I made sure my firewall (zonealarm) was turned off on my winxp machine but still had same problem.  I CAN access my ubuntu shared folders from my winxp computer.  I really want to get this working so my network printer(on the winxp computer) will work for me.
WinXP SP2 has a firewall that's on by default (Start/Control Panel/Windows Firewall).  Turn **that** off.

---

### Post by RxRated on 2008-01-04
I had made sure the firewall was off.  I also have Kubuntu on this laptop, and I was able to access win xp shared folders with it last night.  Problem was it kept asking for a username and password.  I tried using the ones I created in smb...didn't work.  So I tried my windows username and password...didn't work either???  What am I missing?

---

### Post by froy02 on 2008-01-04
try this thread for networking with windows. it worked for me.

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by cyclingman on 2008-01-11
I turned the firewall off, and it still didn't work. Isn't the software on gusty able to share without installing that network thingy (from the link). Is there any other reason for this problem? I will install the program if there is no solution.

---

### Post by cyclingman on 2008-01-14
no?

---

### Post by cyclingman on 2008-01-22
my problem still hasn't been solved??? :(

---

### Post by kirsche on 2008-01-22
make sure your XP doesn't require the guest account to access file shares.
(inidication would be if your own xp account cannnot connect to the share)

---

### Post by cyclingman on 2008-01-31
The xp box can connect to the shared fine (I think), if that's what you mean. Has anyone got any suggestions? Maybe it's a setting I've changed on ubuntu because it used to work about 1 month ago when I was first using Ubuntu. If so, is there a way of me resetting samba etc.?

---

### Post by cyclingman on 2008-02-01
its quiet ...

---

### Post by cyclingman on 2008-02-05
I got it working, yet i can't see the Ubuntu shared folders from my XP box (if I right click, then make the folder shared on my windows network). Anyone got any ideas?

---

### Post by palmdoc on 2008-06-01
After installing and configuring samba, I still couldn't see the shared folders on my Windows XP machine from UBuntu
I tried from Nautilus smb://machinename
The only thing which worked is
smb://IP Address

Something wrong with 8.04?

---

### Post by patricksharpe on 2008-06-12
I was having a similar situation. How I was able to resolve this issue was very simple. The issue doesn't seem to be within the SMB transmission (what allows Ubuntu to access Windows shares) I found out that somehow the network neighborhood (what you browse to see the computers / shares) seems to loose the location of the computers and shares over a network. I haven't figured out what causes it, but I can speculate that when something significant changes over the router (possibly the reacquiring of IP leases or changing DNS routing) could cause the network neighborhood to reset itself resulting in an empty folder or not being able to see any of the computers over the network. What I do now to resolve the situation is simply to reset the router. I can either restart the router by means of logging into it or by cold booting it (cold boot is unplugging the power for 15 seconds or longer to reset the router) Make sure that your computer is still on with its network cable attached to the router when the router resets itself. Once its reset your computer should be able to see Windows shares. I see the issue come up often and each time following this thinking has solved the issue. If your on a very complicated network, meaning more than one switching device and or more than one routing device, you may want to try dumbing down your network to just one switch (for testing this issue) with your windows boxed attached and your Ubuntu box attached. This will eliminate a lot of confusion in trying to test your issue. I know this method sounds very simple but I promise you I was wondering why at one point nothing was working and then suddenly due to some circumstances on my network I found out resetting my router solved the issue. I have 2 Ubuntu 8.10 machines and a single Windows xp box hosting files over a wireless router that feeds into an up link port on a 5 port Linksys switch (a semi confusing "home" network with a lot that could go wrong, but it works just fine with 8.04 as long as you maintain an understanding of basic networking)

---

