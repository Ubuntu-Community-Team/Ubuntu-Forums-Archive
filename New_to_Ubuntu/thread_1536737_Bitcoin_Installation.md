---
title: "Bitcoin Installation"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by adamjkok on 2010-07-22
I just downloaded Bitcoin and it came as a .tar.gz file. What do I do with it? How?

---

### Post by cariboo on 2010-07-22
Just double-click the tar.gz file and select where you would like to extract the archive, I would suggest somewhere in your home directory, then navigate to /bitcoin-0.3.2/bin, the select whichever version you are running, 64-bit or 32-bit, then just double click bitcoin.

---

### Post by sbsgillet on 2011-02-15
Hi,

What i did was the following:
1- Open a terminal
2- type: ```
sudo apt-add-repository ppa:stretch/bitcoin
sudo apt-get update
sudo apt-get install bitcoin
```3- Run application (Alt-F2 will open the application launcher, then type bitcoin)

This will add ppa:stretch/bitcoin to your repositories, to access to the bitcoin repository.
I installed bitcoin this way because when installing from the executables of bitcoin website, a "fragmentation error" occured...
That worked for me on Ubuntu 10.10 (32 bits)

---

### Post by mannyweb.ca on 2011-03-30
> **sbsgillet said:**
> Hi,

What i did was the following:
1- Open a terminal
2- type: ```
sudo apt-add-repository ppa:stretch/bitcoin
sudo apt-get update
sudo apt-get install bitcoin
```3- Run application (Alt-F2 will open the application launcher, then type bitcoin)

This will add ppa:stretch/bitcoin to your repositories, to access to the bitcoin repository.
I installed bitcoin this way because when installing from the executables of bitcoin website, a "fragmentation error" occured...
That worked for me on Ubuntu 10.10 (32 bits)

Thanks I'm running Ubuntu 10.04 (64 bits) and it worked for me.  :)

---

### Post by Willynux on 2011-05-06
> **cariboo907 said:**
> Just double-click the tar.gz file and select where you would like to extract the archive, I would suggest somewhere in your home directory, then navigate to /bitcoin-0.3.2/bin, the select whichever version you are running, 64-bit or 32-bit, then just double click bitcoin.
When I click on bitcoin it asks what software I want to use to open it. None I have tried worked...
The terminal operations above didn't work either. Any other ideas?
I'm running U11.04

---

### Post by erichu on 2011-05-09
Willynux: I'm getting the same thing with Ubuntu 11.04.  Both the executable file and the apt-get approach didn't work.  I believe the reason is that the Ubuntu repo for this software doesn't exist for the Natty version yet.

If you're really intent on installing it, I believe that the command  line operation above (specifically apt-add-repository ppa:...) will add a  repo mapped to ubuntu 11.  I *think* you should be able to specify  another repo by changing

You can access the repo you added by opening up Synaptic Package Manager.  At the top menu, click "Settings -> Repositories" and select the "Other Software" tab.  Look for the repo you added earlier with that command in terminal.  It should look like  "http://ppa.launchpad.net/stretch/bitcoin/ubuntu natty main".  Note that you can visit that [link without the natty main]("http://ppa.launchpad.net/stretch/bitcoin/ubuntu/dists/") and there are directories for maverik and lucid.

Back in the Synaptic settings, you can right click on this link and change the distribution to Maverick or Lucid.  I chose Maverick since it's newer, so I assume it'll be closer to Natty.  After making this change, you can install using the command  (sudo apt-get install bitcoin) or by clicking reload in Synaptic and then searching for Bitcoin.

I've just gotten it installed using this method but I don't see any GUI appearing.  The process shows up in System Monitor, so if you decide to follow this post, maybe someone else can step in and explain where to go from here.

Edit: In the command line, "bitcoin --help" shows a list of commands.  I guess this is a non-graphical program but it looks like my installation is functional.  Now to read up on bitcoin some more so I can use this...

---

### Post by the.scarecrow on 2011-05-10
There is a problem with bitcoin in Natty in that the GUI doesn't work in Unity. Bitcoin does run but thats not much use if you can't see it.

There is a bug report you can add your name to and a temporary work around is to switch to Ubuntu classic desktop.

---

### Post by erichu on 2011-05-12
@the.scarecrow thanks for that info.  I think another workaround is to manually edit the config file or use bitcoind (command line).  I'm too lazy for all those solutions, though =P  Did you add your bug report to Bitcoin or to Unity?

---

### Post by rat9 on 2011-05-16
I am in ubuntu 11.04 32bit classic gnome desktop and i downloaded the files from the website and executed the binary and i get no GUI but it shows in system monitor.

---

### Post by graphius on 2011-05-17
I am using 64-bit Natty. I thought I would play around with bitcoin, but, as with others here, I can't get it to work. After adding the Maverick ppa, I installed bitcoin, then tried to run bitcoin from the command line (as nothing showed up on my menu in classic gnome) the terminal just locks up.

---

### Post by pengper on 2011-05-18
I'm another one with the 11.04 32bit problem- just got it and thought I'd give it a whizz, and it doesn't open. Would give you a screenshot but I'm new to Ubuntu (2 days an owner) and I don't know how :oops: but it says "Could not display "/home/pengper/Documents/BTC/bitcoin-0.3.21/bin/32/bitcoin"." and "There is no application installed for executable files". If that's any help :P

---

### Post by graphius on 2011-05-18
I found the solution on the bitcoin forums [here]("http://forum.bitcoin.org/index.php?topic=6299.0")

at the bottom of the first page BlueMatt posted a solutin that works for me...

---

### Post by pengper on 2011-05-18
Thanks a bundle, that's solved it in one! 

Cheers :D

---

### Post by art_erickson on 2011-05-19
I appreciate the get commands, too bad getcoin doesn't work with Unity :(

Is there another command to add the ppa to the Ubuntu Software Center?

---

### Post by aarongc on 2011-05-19
As I posted above, bitcoin works on my 32-bit Natty laptop. Just tried it on a 64-bit desktop, and no go. Got a window saying:

An assertion failed!

../src/gtk/tbargtk.cpp(263): assert "bitmap.IsOk()" failed in SetImage(): invalid bitmap for wxToolBar icon

So looks like this may be an issue only affecting 64-bit.

EDIT: Erm, sorry guys, looks like I didn't hit "submit" on my post yesterday. Also, I have not tried BlueMatt's solution.

---

### Post by art_erickson on 2011-05-19
> **aarongc said:**
> As I posted above, bitcoin works on my 32-bit Natty laptop. Just tried it on a 64-bit desktop, and no go. Got a window saying:

So looks like this may be an issue only affecting 64-bit.


Alas, I run AMD 64 bit.

---

### Post by Willynux on 2011-05-28
Post #12 worked for me, thx

---

### Post by Krain on 2011-05-29
Thanks for the link. This worked great.

---

### Post by John Bennett on 2011-06-15
> **sbsgillet said:**
> ```
sudo apt-add-repository ppa:stretch/bitcoin
sudo apt-get update
sudo apt-get install bitcoin
```

This worked for me.  Thanks!

Next, I right-clicked on my desktop and selected "Create Launcher..."

In the "command" field of that dialog I put "bitcoin", and it works.  It even has the Bitcoin logo for an icon.


Now please somebody send 0.0000000000000001 Bitcoins to [FONT="Courier New"]1MYvirChyqPX9RaPVMMnjBFyT1B69vVdfs[/FONT] and your good karma will be increased. :D

---

### Post by kmsalex on 2011-06-16
Can you mine with just this? I was under the impression you needed another miner in conjunction with it. If you can, how do you do you connect it to a pool worker? the options seam nearly non existent!

---

### Post by hippi80 on 2011-06-18
I didn't have any trouble getting bitcoin to work.  it's getting a miner to work i can't figure out.  I'll do some more research but if anyone has a good link it would be greatly apreciated.  thanks!!!

---

### Post by bobbr on 2011-07-24
I went into System Monitor and killed the bitcoin process. then in terminal used:

bitcoin -gen

worked.

---

### Post by Donnie Love on 2012-09-14
"select whichever version you are running, 64-bit or 32-bit"

How do you find out which you have?

---

### Post by SlugSlug on 2012-09-14
I dont get this bitcoin, where can you spend coins

Do ppl recomend it? Am looking for a replacement to paypal for an online game

---

### Post by oldos2er on 2012-09-14
Old thread closed.

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

