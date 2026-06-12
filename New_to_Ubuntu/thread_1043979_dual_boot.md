---
title: "dual boot"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by ericgds on 2009-01-19
Hi. I am trying to dual boot ubuntu and windows xp after having downloaded ubuntu while accidentally erasing windows completely. Treesurf sent me a great link that explained it step by step but I am stuck.

Everything worked Ok until I tried to reinstall the grub.
I type in setup (hd,0) and it says error 17: cannot mount selected partition.

I tried posting this earlier but Hymntolife (a very rude and unhelpful staff of the forum) tells me they don't help w/ pirated software and shuts down my 
thread.

So what do I do hymn?  I don't have pirated software but since you think I do and I'm screwed. Without help I guess I just go buy a new computer.  Thanks.  I'm beginning to deeply regret trying umbutu as I've had nothing but headache and now my computer barely works.

---

### Post by Temposs on 2009-01-19
What OS's do you have installed right now?

---

### Post by cjv8888 on 2009-01-19
How did you erase Windows?
Did you delete the partition?

---

### Post by ericgds on 2009-01-19
> **Temposs said:**
> What OS's do you have installed right now?

Right now I have the cd of umbutu.  It's the only thing on my computer that makes it work since after reinstaling xp and getting stuck before finishing the grub thing, neither xp or the previously downloaded ubuntu works.

---

### Post by ericgds on 2009-01-19
> **cjv8888 said:**
> How did you erase Windows?
Did you delete the partition?

I downloaded ubuntu due to advice i got after being frustrated with a virus on windows.  I must have went too fast because I didn't know I wasn't allowing for a windows partition.  I also didn't know I had to be some kind of cumputer whiz to use ubuntu either.  I should have researched but the virus frustrating me and I pulled the trigger on ubuntu to soon as (so far) ubuntu makes a virus seem like childsplay when it comes to the frustration level it causes.

---

### Post by Temposs on 2009-01-19
ericgds,
   I am sorry you are having trouble with ubuntu so far. It can be a little difficult for people that are used to using Windows. But, I think, once you get past a few trials, it may turn out to be very nice for you.

Here is what I would personally recommend.

I recommend for you to reinstall Windows XP over Ubuntu, so that Windows XP is using the whole hard drive, and there's no trace of Ubuntu.

If, after you get Windows running, you want to try using Ubuntu, then try to install Ubuntu again, but this time make sure you are leaving room for Windows. The install process allows this pretty easily with a graphical slider. Try this tutorial on using the graphical installer: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Pay special attention to the "Select a Disk" section of this tutorial. In this way, you should be able to install Ubuntu using a portion of your HDD that you wish to use, without erasing Windows XP.

Ubuntu is not simply a software product. It is a community. There are many people on here that are willing to help, and you are good to try again if one person is unhelpful to you.

---

### Post by ericgds on 2009-01-19
> **ericgds said:**
> I downloaded ubuntu due to advice i got after being frustrated with a virus on windows.  I must have went too fast because I didn't know I wasn't allowing for a windows partition.  I also didn't know I had to be some kind of cumputer whiz to use ubuntu either.  I should have researched but the virus frustrating me and I pulled the trigger on ubuntu to soon as (so far) ubuntu makes a virus seem like childsplay when it comes to the frustration level it causes.


I give up.  i'm going to bed and hope that the umbutu fairy will have given me a magical answer on this forum by the time I wake up.  on second thought, maybe I'll come to my senses and buy a new computer with windows since ubuntu has helped me to make mine useless.

---

### Post by Temposs on 2009-01-19
> **ericgds said:**
> I give up.  i'm going to bed and hope that the umbutu fairy will have given me a magical answer on this forum by the time I wake up.  on second thought, maybe I'll come to my senses and buy a new computer with windows since ubuntu has helped me to make mine useless.

There are also new computers that come with Ubuntu. Both Dell and System76 have them. Here are a couple of links:

[http://www.system76.com/](http://www.system76.com/)
[http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs](http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs)

If you buy one of these, you do not have to worry about installing Ubuntu. It will come with everything you need, just like if you bought a computer with Windows. However, I would recommend to try my method that I suggest in my previous post first. 

You should not throw away a whole computer just because the operating system gets messed up, if the hardware is still good. Software problems can be easily remedied by an expert. Take it to someone who knows computers(a friend or a computer repair shop) to reinstall your operating system instead of buying a new computer.

---

### Post by bailbath on 2009-01-19
> **ericgds said:**
> I give up.  i'm going to bed and hope that the umbutu fairy will have given me a magical answer on this forum by the time I wake up.  on second thought, maybe I'll come to my senses and buy a new computer with windows since ubuntu has helped me to make mine useless.
Well have a nice sleep.
All I can say to you is all is not lost.
Perhaps you can give us a few more details of your computer and the guide you used to install ubuntu.A bit of time will save you buying a new pc then you can use the money for beer.
Ubuntu did not make your computer useless, your computer is not useless it is misconfigured just needs to be corrected. Do you want to install both XP and Ubuntu?
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Do you want to install just Ubuntu? I don't know which version of Ubuntu you have but I recommend getting the long term support version 8.04.[http://en.wikipedia.org/wiki/Ubuntu](http://en.wikipedia.org/wiki/Ubuntu)
Install guide
[https://help.ubuntu.com/8.04/installation-guide/i386/index.html](https://help.ubuntu.com/8.04/installation-guide/i386/index.html)
Plus you can get guidance from this forum.
Ian

---

### Post by caljohnsmith on 2009-01-19
Ericgds, in order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

