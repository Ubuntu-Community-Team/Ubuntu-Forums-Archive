---
title: "Unusual and Odd Problems with 9.04.amd especially 9.10"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by lhb1142 on 2009-11-02
I apologize in advance for the length of this thread but I hope someone can help me.

My wife and I have two Acer Extensa 5620-6419 computers. We have both been using Ubuntu since last year. With 8.04 'Hardy Heron' there was only one problem - the delete key wouldn't work - but that was quickly fixed via an update.

When 8.10 'Intrepid Ibex' came out, having read that clean installs were better than network upgrades, I wiped both of our computers with DBAN and installed 8.10. With that version, we had absolutely no problems.

I did do a network upgrade on my own computer to 9.04 "Jaunty Jackalope" and found one unique problem: while I could still burn CDs via an external drive, I could not burn DVDs with it; I could burn them with the computer's internal CD/DVD drive. (I tried several external drives and got thee same results with all.)

I then wiped my computer again and did a clean install; the same problem persisted (everything else worked fine,, however).

I posted several questions both here and on the Lauinchpad forum about this problem with 9.04 (I even made a bug report) but I never received even one answer.

Now with "Karmic," I have a major problem. I did a network upgrade on my computer and the first night, everything worked perfectly for several hours; anything I wanted to do, I could do. It is much faster, and appeared to be far better than any other version thus far. I had planned  to try to burn a DVD with an external burner the next day.

But the next day, I could no longer get onto the internet with Firefox. This is very strange! Why all of a sudden when I had had no problems at all the night before? My internet connection is fine and I could even check (and get) updates via the Update Manager; I was even able to play certain internet radio stations whose URLs I had saved in my Music folder. Obviously I was connected! But I could not get on the web at all.

I did a clean install on my wife's computer - with similar results. At first our selected home page would partially download, but, after fiddling around a bit, it would not even do that.

I wiped my computer, did a clean install, and - the same thing.

Everything else works perfectly; updating is no problem.

What could be wrong?

In the mean time, I wiped both of the computers and I reinstalled 8.04 'Hardy Heron' on my wife's computer (and everything works perfectly, as it did last year) and I'll do the same on my own unit tomorrow.

Does ANYONE have any ideas concerning this major problem? What worries me is that, if this "normal" release cannot be fixed, will the next release which is a LTS be any  better? Support for 8.04 ends in April 2011 and I'm getting concerned, having had problems with the last two releases.

I'm writing this from an Asus EeePC 1000/Linux machine so I hope you'll pardon any typos.(The title has a typo and I can't correct it.)

Thanks for reading this and thanks for any help anyone can provide,

---

### Post by anewguy on 2009-11-02
Did you ever reboot after the update, or was this the first reboot?  It's possible your wireless drivers are "lost".  Post the output of lspci here and we'll check.  There are a couple of small things I found about for 9.10:

If you are using an atheros chipset in the wireless, as su, edit the file /etc/modprobe.d/blacklist-ath_pci.conf and and change the following line:

blacklist ath_pci

to

#blacklist ath_pci

Save the file, exit the editor and reboot.


For other chipsets, check in system/administration/hardware drivers and see if a restricted wireless driver shows there.  If it is not enabled, check it and enable it.

These are the 2 things I found from watching other posts so far.

BTW - with network manager, are you seeing any wireless networks?

Dave :)

Just re-read your post after my reply posted, and see that you can get to the net, just that FireFox won't "see" anything.  Check under "file" and see if it is working off line.

---

### Post by yeats on 2009-11-02
> When 8.10 'Intrepid Ibex' came out, having read that clean installs were better than network upgrades, I wiped both of our computers with DBAN and installed 8.10. With that version, we had absolutely no problems.

To do a "clean install" it is not necessary to completely wipe your computer, for future reference.  The Ubuntu partitioner takes care of that when formatting the partitions you are using.

> I posted several questions both here and on the Lauinchpad forum about this problem with 9.04 (I even made a bug report) but I never received even one answer.

I think your posting style may be working against you in this.  You might consider boiling down your problem to a brief description of your problem and a question - the more specific, the better.  (In my non-computer life, I am a librarian, so trust me on this :-) ).

>  But the next day, I could no longer get onto the internet with Firefox.

If you try Karmic again, can you provide more specifics?  You could also try another browser, such as Epiphany (the default GNOME browser) to see if that works.  If so, you would know that the problem is specific to Firefox and would not require a complete reinstall.

> Does ANYONE have any ideas concerning this major problem? What worries me is that, if this "normal" release cannot be fixed, will the next release which is a LTS be any better? Support for 8.04 ends in April 2011 and I'm getting concerned, having had problems with the last two releases.

I don't have any specific advice (especially since it looks like you've already moved back to Hardy) except in general that you might consider giving a new release a little more time to get the kinks out.  That will include the LTS this spring.  

In the meantime, if you can make your postings more specific, I think you'll get useful responses.  Good luck!

---

### Post by lhb1142 on 2009-11-03
):P  Thank you all for your replies. I wiped my wife's computer and reinstalled Ubuntu 8.04 'Hardy Heron' - but she HATED it (and told me so in no uncertain terms! We had both previously been using 'Jaunty').

So, having previously wiped my own computer, I decided to try to install 'Karmic' one more time - and this time it's working fine.

The only difference in my first installation (with which Firefox would not load any pages - even though my wireless internet connection was fine) and my second, current, installation is that I did NOT install a program called Ubuntu Tweak. We had been using this particular program for the past several months and had no problems with it but it may be conflicting with something in 'Karmic.'

In any case, there is no need for it; right in the Synaptic Package Manager (all included sources activated and with Medibuntu in the Software Sources as well as the Canonical ones) there is a program called BleachBit which does essentially the same cleanup things that Ubuntu Tweak did. It comes in two "flavors" - regular and "as root." I tried them both and they both work splendidly.

I have now spent the last four days playing around with this; I hope that this is it! (Of course I still have to install 'Karmic' on my wife's computer since I wiped 'Hardy' off it today - she had to go a WHOLE DAY computerless! Can you imagine?)

Thanks again!

---

### Post by lhb1142 on 2009-11-05
The problem was not, as I thought, solved. The Firefox anomaly only showed up on the SECOND day following installation of 'Karmic.' I put a query (and a Bug report) on the Launchpad forum and I received two replies, both of which have apparently - apparently - solved the problem, which recurred today.

To fix the Firefox anomaly (not loading pages even though I was definitely connected to the internet), I did two things:

First, in the Terminal, I ran:

mv ~/.mozilla ~/.mozilla_old

This removed my previously installed Firefox and replaced it with a pristine new one

and then I:

1.Type about:config in the address bar, press Enter.
2. Find network.dns.disableIPv6 in the list.
3. Right-click -> Toggle. Set to true
4. Restart your Mozilla application and try again.

These answers were sent to me by two members of that forum Actionparsnip and Wojox to whom I am very grateful.

This appears to have solved the problem as Firefox is connecting just fine.

Of course I won't REALLY know until tomorrow, but at least I know how to reconfigure Firefox should the need arise again.

---

### Post by lhb1142 on 2009-11-06
The problem is totally fixed. Wojox's solution did it. I posted a 'bug' report on the Launchpad forum and it is being investigated.

I hope that no one else has this problem (it may be caused by turning off your wireless router as well as your computer; when both are restarted, something conflicts and will not allow Firefox to load MOST pages; in my case it did allow SOME pages to be loaded. Very strange, to say the least!).):P

---

