---
title: "Newb needs help constructing media server"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by Brimace on 2010-01-11
Hello world, 

This is my first post ever to the forums so be nice.

Here's my situation:

I have a wireless network set up through an apple airport extreme base station. connected wirelessly to the base station is my intel imac and my 80gb PS3.

I want to convert an old dell dimension 8200 (2ghz pentium4, 512 mb ram)into a media server that will always be on and will stream to both my imac and my PS3. I also want to make it so that I can rip movies from a dvd, and music from a cd automatically by inserting a disc into the drive. also...It would be nice to have a bittorrent client on it.

I've been trolling for a while, but I haven't started yet. I plan on trying a few different configurations on the dell before I spend the money to upgrade the hard drives to a bigger size. However, I would love to get it right the first time.

So far, I've decided to go with Ubuntu Server edition 9.10 unless someone tells me otherwise. 

so, how should I do this. keep in mind, I've never touched linux before but I'm not afraid to get dirty with command line computing.

Any help will be appreciated, I'll give updates on my progress.

-Bryce

P.S. I am aware of the following options: vortexbox (I don't think it was all of the functionality i want though), mediatomb, abcde, fuppes, ps3 media server (got it to semi work on my imac). so I have some pieces, but I don't know how to fit them together yet.

---

### Post by dream_coder on 2010-01-12
Why are you going to use Ubuntu Server edition when you just want a media-server?

Unless you are planning on using other services ie Web Server, FTP etc I recommend you use Ubuntu Desktop Edition Especially as You are new to linux and Linux Server comes with no gui installed by default (not that it is difficult to install afterwards)

Mediatomb Works flawlessly with the ps3, not sure about mac, I would just use that for streaming media, I would also recommend you use Deluge as torrent client and then just set up a folder on desktop for example that deluge auto imports .torrents from and then unrars them to another directory etc, all in all will be very easy to do except the auto rip dvds and cds, shouldn't really say that in this forum and I doubt you will receive any help with that.

---

### Post by egalvan on 2010-01-12
Can't really help with specifics, as I don't "stream media" at home...

but I can give some general ideas...

first, you will probably NOT get it right the first time... :)
you will probably find yourself tweaking the system.

Second, running a stock Server Version means that you will run in Command Line Mode.
It is trivially easy to install a Desktop Environment, such as Gnome or KDE,  by the way...

*dream_coder* asks: Why are you going to use Ubuntu Server edition when you just want a media-server?
I recommend you use Ubuntu Desktop Edition...


to which I would further ask...

Why are you going to use Ubuntu Desktop Edition when you just want a media-server?

Well, the Server edition has much less bloat.
It is easier to install Server and build it up (add what you need) than to install Desktop and remove what you don't need.

... having said that, it is even easier to install a minimal Ubuntu and build from there.


Then there is MythBuntu, which may or may not meet your needs.

Install with separate partitions for root, boot, swap and home
(/, /boot, /swap, /home).
You can even put the /home on a separate hard drive, to keep all user data separte.
This will help in the long run.
(on one server install, i even put GRUB in it's own partition)


As for your hardware, the CPU is probably adequate, unless it is a Willamette core, or any Celeron,
 in which case I would recommend up-grading to a full Northwood-core P-IV.
They are cheap on eBay... I've had excellent luck with amdrecycling, out of Richardson, Texas.
My spec sheet shows a Socket-478, either Willamette or Northwood core...
 go for the Northwood, it's faster, cooler and has a larger cache..
Willamette is older, slower, hotter and cache is limited to 256K.

As for the 512M of RAM, I would definitely try to upgrade to at least 1GB.
(Do you NEED that much? No. But it will make for a smoother-running machine.)
My spec sheet on the 8200 shows that is uses Rambus memory,
which is woefully obsolete, which is good and bad...
Good: Some sellers give it away "because it's so old",
Bad: Some consider it "rare" and charge accordingly..
you will have to look around.


And since it an older machine, I have one further word of advice...

**CLEAN IT OUT**

It probably has many years worth of dust bunnies hiding in the case, power supply, heat-sink fins, etc, etc, etc.

DON"T use a brush, use compressed air. Take it to a gas station or mechanic who will let you use their compressor.

One by one, disconnect and reconnect all the connectors,
this will help remove any oxidation from the contacts.

Good luck.

EGalvan

---

### Post by Brimace on 2010-01-12
Another thing I found out, Airport Extreme doesn't support UPnP. How can I solve that?

Update: Well that didn't take long to experience my first "problem" I had the 64bit version iso on the cd not the 32bit. oops.

Update 2: Ok, I installed Ubuntu server 9.10 32bit version. I installed all the package options listed on the installer, because: a: i don't really know what I'm doing, and b: might as well have it all available when someone tells me I need it. 

After installation I'm greeted with the terminal and I am up for the challenge, but I admit, I had a slow wave of dread fall over me as I realize I have no idea how to do anything right now.

So whats my next step? I assume that I need to join the network somehow and test the connection between them. how would I do that?

---

### Post by Brimace on 2010-01-12
Ok, So I found this tutorial online:

[http://www.maclife.com/article/howtos/how_make_your_pc_media_server?page=0%2C0](http://www.maclife.com/article/howtos/how_make_your_pc_media_server?page=0%2C0)

in which it says to:

[I]"Now you need to test the SSH connection. First, take note of your IP address. To do this, go to Terminal and type 

*ifconfig*

You will see a long string of text, but the important thing to note is what comes after "inet addr:" This is your server's IP address.  

Now, go to your Mac and open up its Terminal (Applications > Utilities > Terminal). Type: 

*ssh {your username on linux}@{the ip address of your linux server}*

It should ask you to add the RSA key to a list of trusted ones. Type 'yes.'

Now, you should be able to run commands as if you were typing them into the Linux computer directly. You can test this by running sudo aptitude update -- this will only work if your ssh connection works.

If you're so inclined. you can now use SSH for the remainder of the steps."[/I]

I wish it worked that well for me. this is what I got:

[I]"Bryce-Hansons-imac:~ brycehanson$ ssh bryce@127.0.0.1
The authenticity of host '127.0.0.1 (127.0.0.1)' can't be established.
RSA key fingerprint is 96:2a:87:b9:9b:95:95:89:73:21:31:fb:48:d3:4b:20.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '127.0.0.1' (RSA) to the list of known hosts.
Password:
Password:
Password:
bryce@127.0.0.1's password: 
Permission denied, please try again.
bryce@127.0.0.1's password: 
Permission denied, please try again.
bryce@127.0.0.1's password: 
Received disconnect from 127.0.0.1: 2: Too many authentication failures for bryce"[/I]

Why isn't it recognizing my password?:(

---

### Post by agillis on 2010-01-25
VortexBox will do everything you described. I will not rip protected DVDs. You need a commercial program to do this.

---

### Post by nerdy_kid on 2010-01-25
> **agillis said:**
> VortexBox will do everything you described. I will not rip protected DVDs. You need a commercial program to do this.

um no.  Ripping dvds is very easy but also illegal if you dont own the dvd you are ripping, and in some places even if you do own it it is still illegal.  

consider: handbrake on linux. (with libcss2)
          handbrake on windows (with DVD4FREE [http://www.dvd43.com/]("http://www.dvd43.com/"))

---

