---
title: "Help older guy with Linux"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by rb3cats on 2009-05-04
Hi I am a new Linux user .I have installed Dapper Drake ^.o6 ( Yeah it's old but so's my machine ) and it runs fine  But I have problems with the command line .I can't install a lousy Firefox update .When I open the terminal and type in the command AS I SEE IT ,It Always says "command not found  " When i treid to insatall a package with the Synaptic manager , I got dpkg--configure-a .So i type it in and it says command not found .How do you get the command line ot work ? I  am a 8 year Windows user who'd rather stay with Linux ,52 yo male and fairly with it .Thank you 
Macihne iHP 12 year old 40 gb hd Celeron cpu

---

### Post by jerrrys on 2009-05-04
52 hu...well dont really like dealing with kids, but guess ill give it a try...

you didnt post your system specs, but would you be willing to give 804 a try?

i know this isnt in your op, but 804 is for the most part great and it just works...

---

### Post by 123456789123456789123456 on 2009-05-04
how much ram does the machine have, have you tried xubuntu?

You are trying to upgrade firefox, through command line?
What command are you tryiing that says command not found?  If I knew the command, I could possibly figure it out.  You are correct, that is a very old distribution.  That could be the problem there.  As far as I am aware, it is no longer supported, so the distribution could be experencing problems with repositories.  Upgrading to xubuntu would probably be best.
Min requirements, to run live cd, you need 192mb ram, to run after install, you need at least 128mb ram
you said it had a 40gb hard drive, that would lead me to think, it has at least 128mb ram
if so, you can download the alternate install cd, of xubuntu.  If you can't find it from the xubuntu.org page, I could give you a link for download.

---

### Post by overdrank on 2009-05-04
Hi and welcome, moved to Absolute Beginner Talk

---

### Post by ubuntu27 on 2009-05-04
Open the [terminal]("http://www.psychocats.net/ubuntu/terminal")

and type (you can copy and paste)

```
**sudo** dpkg --configure -a
```

The only times you need to put the command is when the the upgrades or installation of a package were interrupted by either canceling or shutting-down.

After you enter that code, you should be able to use Synaptic Package Manager without issues.

[How to install software in Ubuntu Linux]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by mprince on 2009-05-04
Make sure that you type the spaces between the commands and options. They are important. If you don't, you will get errors.

---

### Post by TheNosh on 2009-05-04
ubuntu is my distro of choice for modern hardware, but on a 12 year old machine i'm not sure it's the best idea, even Xubuntu.

---

### Post by rb3cats on 2009-05-09
Thanks to all for advice .I ran the sudo and that helped the synaptic package problem I am looking for a newer machine for more ram ,I only have 128 in this HP. I am going to dl xbuntu and burn it off to try ..I will let you know of any further issues thnx:)

---

### Post by rb3cats on 2009-05-09
Okay guys .I ran the command for thr firefox update as sudo firefox -3.0.10.tar.bz2 I got an answer saying " You should use the -H option but I'll run it as though you did " .Then the page goes to the Ubuntu start page .When I go to The Firefox page ,I get a message to upgrade to Firefox three as though I never ran the command .Any ideas :confused:

---

### Post by swoody on 2009-05-09
Hi rb3cats, and Welcome to Ubuntu and the Forums ):P

When you go to the Firefox page, do you mean their website? It may just be an advertisement for anyone out there to upgrade to Firefox3. Or is it an actual message you are getting on your system? I would agree that Dapper Drake is no longer supported, so you may run into a plethora of issues in the future trying to get this version to work. You may want to try Xubuntu as previously mentioned, or even another distro such as [Damn Small Linux]("http://damnsmalllinux.org/") or [Puppy Linux]("http://www.puppylinux.org/") if Xubuntu is still too heavy for your system. I'd recommend trying Xubuntu first, though.

If you are interested, I have a link in my signature to the Free Ubuntu Guide. This is a great guide to have on hand while you're learning about Ubuntu, and getting used to everything. You can either just download it to your computer and reference it as you need, or even print it out and have a hard copy nearby while you use your computer. I just thought I'd toss it out there for you :)

Either way, it's good to see you on the forums! Don't be afraid to ask questions on here! :D

---

### Post by rb3cats on 2009-05-09
Firefox -I downloaded the file from their website to upgrade .It wasn't an advert .I tried to run and got the message from the terminal about -H option When i ran help ,that -H option wasn't listed But ok maybe I need to go to xbuntu

---

### Post by rb3cats on 2009-05-09
Hello me again When installation of packages is ocurring ,the terminal window opens up and shows that the vmware player and vmnet failed .The exact phrase is vmnet module needed and virtual monitor failed What's the fix ? I looked in packages with advanced search but didn't see vm module

---

### Post by ugm6hr on 2009-05-09
I would urge you to install a newer version of (X)Ubuntu, since Dapper will not be supported on Desktop for much longer.

FF3 is default on all current Ubuntu versions.

As mentioned, even Xubuntu will be slow with 128MB RAM, but is worth a try.

---

### Post by 5carby on 2009-05-09
Wouldn't Slackware work better on his machine?

---

### Post by JC Cheloven on 2009-05-09
Hi r3bcats, and welcome. Another old guy here ;-)

As the wise people here told you: using an old unsupported distribution is asking for problems (given that you want to perform updates afterwards). Here is that I would do:

1) Of course, save your sensible data to an external media.
2) Partition your disk first, creating a swap area of 512Mb. You can use [gparted live]("http://gparted.sourceforge.net/download.php") disk for that.
3) Try the distribution you like. It will probably run from livecd despite your scarce ram, as it will probably use the swap. Eventually install, and see how slow/decent/fine it runs.
4) Repeat step 3 until you're satisfied :-D

People's advice about xubuntu could be nice, but it is heavier these days than it used to be. I'd give a try at ubuntu directly (9.04, 8.10 or 8.04.2 LTS). On the other hand, there are plenty of lighter options in linux. DSL and Puppy (someone mentioned) are fine and really light.

But if you'd rather ro remain a bit closer to ubuntu while staying on the light side, i'd suggest to try [crunchbang linux]("http://crunchbanglinux.org/"). It's a little experimental yet, but is ubuntu-based and I've found it to perform fine using far less resources.

Regards

---

### Post by pbpersson on 2009-05-09
> **rb3cats said:**
> I  am a 8 year Windows user who'd rather stay with Linux ,52 yo male and fairly with it .

Older than who?  You are younger than I am :)

---

### Post by OurSpace on 2009-05-09
I would suggest a live version burnt to a cd. Does Ubuntu have a live cd? I would order (I think I seen a website where you can get different versions of linux on cd shipped to you for a dollar a piece) get several different ones, boot with them, and see which one works best for your machine, then install that on the computer, or just run a live version booting from the cd all the time. Also, I like to open a terminal and type 'SU" then root username, and root password, and work in that terminal window as root  (for such things as synaptic, apget, etc..) but that's just me.
I hope this tidbit of info helped you in some way, if not sorry.
OurSpace

---

### Post by ugm6hr on 2009-05-10
> **OurSpace said:**
> I would suggest a live version burnt to a cd. Does Ubuntu have a live cd?

Yes Ubuntu has a LiveCD.  But it won't run on 128MB RAM.

Even Xubuntu LiveCD requires 256+, although it will run once installed from the AlternateCD (with a swap partition).

As explained, a minimal Ubuntu with LXDE (or Crunchbang - though I have never tried it) or an alternative such as Puppy Linux will be faster.  AntiX is another nice alternative, and is Debian / Mepis based (and therefore has a large repository like Ubuntu).

The main point is to try and find an alternative to Ubuntu 6.06, which will be unsupported soon; therefore, spending time to resolve issues with it is not time well spent.

It is always difficult to recommend minimal Linux distributions to relative beginners, since they are not as "friendly" as Ubuntu; nevertheless, Puppy and AntiX are good choices in this respect.

@r3bcats:
I hope this is not confusing you.  Essentially, there are multiple options for your computer, but your current choice of Ubuntu 6.06 is universally not recommended at this stage.  I would suggest browsing the Puppy, AntiX and Crunchbang websites to see if any catches your eye.  It will not cost much to download and burn CDs for all of them to try them out.  If you want to stick with an Ubuntu-base, then Crunchbang ot Xubuntu are your best starting points.

---

### Post by rb3cats on 2009-05-25
Hello again . I took some advice and downloaded  Xubuntu and installed it on my sad old machine .It is the brand new distro and it works fine .It does updates through Update Manager and I upgraded to Firefox 3.0 .and installed the media codecs for the Totem Movie player .I didn't use the command line at all ,which probably might disturbed some of you old time users .But it will keep me in Linux because of the ease of updating things I want to have ,rather than WIndows doing it for me .My Firefox ,Rhythymbox player and Totem player works fine .I willl have to get a better machine tho .But for now ,it's all good ! :D:D:D:D:D:D

---

### Post by albinootje on 2009-05-25
> **rb3cats said:**
> But it will keep me in Linux because of the ease of updating things I want to have ,rather than WIndows doing it for me .My Firefox ,Rhythymbox player and Totem player works fine .I willl have to get a better machine tho .But for now ,it's all good ! :D:D:D:D:D:D

Excellent! :)

And as a reminder for your better machine in the future, please make sure that you buy a machine which is well supported by Linux.
With that you will basically show as a consumer that you care about Linux support.

Where are you located ? Here's some pre-installed Linux hardware vendors :

[http://www.linuxemporium.co.uk/products/laptops](http://www.linuxemporium.co.uk/products/laptops)
[http://system76.com](http://system76.com)
[http://www.zareason.com/shop/home.php](http://www.zareason.com/shop/home.php)
[http://www.dell.com/content/topics/segtopic.aspx/ubuntu?c=us&cs=19&l=en&s=dhs&~ck=anavml](http://www.dell.com/content/topics/segtopic.aspx/ubuntu?c=us&cs=19&l=en&s=dhs&~ck=anavml)
[http://www.linuxcertified.com/linux_laptops.html](http://www.linuxcertified.com/linux_laptops.html)
[http://os4free.nl](http://os4free.nl)

And not sure how up-to-date this page is, but that has a whole list of them in various countries worldwide :
[http://www.linux.org/docs/beginner/preinstalled.html](http://www.linux.org/docs/beginner/preinstalled.html)

---

### Post by lisati on 2009-05-25
> **rb3cats said:**
>  I  am a 8 year Windows user who'd rather stay with Linux ,52 yo male and fairly with it .

Hi there, and a belated "welcome to the forums". Feel free to ask questions and share your wisdom.

52 isn't old.... You'd better watch out: I'll be catching up in about 3 & 1/2 years.....

---

### Post by rb3cats on 2009-05-26
Hello It's me again with a new tale of woe ....:(
After installing Xubuntu and using it happily for a few days I booted up and .............NO Desktop Icons ! I do get Firefox  and the net tho .I rebooted in recovery mode and did a memtest .Both tests went well .What happened guys and what can I do ? Ps It's 9.04 the NEW version  HP Celeron 128 ram etc. Think I need a new machine ? LOL

---

### Post by ugm6hr on 2009-05-26
I haven't used XFCE for a while now, but have found it a bit hit and miss re: stability on the desktop.

Occasionally, the panels disappear, and the desktop settings change spontaneously.

If right-clicking on the desktop does not allow you to set thunar to control the desktop again, try posting in a new thread with a relevant title about Desktop icons on XFCE.

---

### Post by samden on 2009-05-26
(deleted)

---

### Post by mkvnmtr on 2009-05-26
I have installed on several machines that came with 128MB. xfce4 from a minimal install is the only one I got to run well. With another stick of ram Ubuntu is fine on those machines. 256Mb will work but 512Mb is great. It probably has a space and won't cost more than 20 dollars american. The machines I am talking about were about the same age and celeron M and R.

---

### Post by raydeen on 2009-05-26
If a new machine is out of the question at this time, maybe some more memory can be bought at a cheap price. Try going to [http://www.crucial.com](http://www.crucial.com) and see if you can find the model of computer you're using (they have a really nice drop-down menu system for finding what you have and what you need) and then see if you can get a memory upgrade for it. Memory is really inexpensive right now and maybe you can plunk down a few $$$ and breathe some new life into the old machine.

---

### Post by Mark Phelps on 2009-05-28
Tried Ubuntu on an "older" HP laptop with a P3 600MHz and 256MB of RAM and it ran so slow as to be all but useless.  Replaced it with Xubuntu (7.04) and it worked but it was still slow.  Was not able to upgrade beyond that due to the later versions requiring more resources.

And, BTW, please open a new thread when you have new problems ... and use a title descriptive of the problem.  It helps folks like me when we're strolling through the forums looking for problems we know how to solve.

---

### Post by andrew.46 on 2009-05-29
Hi ugm6hr,

> **ugm6hr said:**
> I haven't used XFCE for a while now, but have found it a bit hit and miss re: stability on the desktop.

Although this discussion is moving a little far from the original discussion I would just like to chime in at this point with a short defence for xfce. I have used xfce exclusively since July 2007 with none of the problems that you have mentioned, although I recognise that this might be the time period that you did not use xfce :-). Mind you this has been with slackware's xfce not xubuntu which I guess in the Debian / Ubuntu way may have been extensively patched?

My apologies for dragging this discussion too far from the original question!

Andrew

---

### Post by ugm6hr on 2009-05-30
re: XFCE (trying not to go too off topic)

I should have explained better; I used XFCE 4.4 on Xubuntu 7.04 (Apr 2007), and found disappearing panels which had to be manually launched at startup.  Easily solved, but annoying at the time.  I was also suspicious of a memory leak, since prolonged use (i.e. >24 hours) would lead to problems.

Nevertheless, I changed to Gnome at 7.10 (Oct 2007) for other reasons, but found none of these problems; hence my comparison above.

I have used Xubuntu 8.04 since then, albeit on a much less regular basis (on a redundant work computer), and not seen any problems with it.

I appreciate XFCE is now 4.6, so may well be much better.  That being said, I might try it out on my Mini 9 netbook...  If thunar had built-in network browsing, I would certainly swap back in a flash!

---

