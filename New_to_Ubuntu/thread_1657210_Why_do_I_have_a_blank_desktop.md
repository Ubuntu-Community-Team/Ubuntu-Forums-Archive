---
title: "Why do I have a blank desktop?"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by MargaretA on 2010-12-31
I've been trying to install Ubuntu 10.10. And trying, and trying, and trying.

OK, how to make this long story (reasonably) short...

1) I wanted to try out Ubuntu on one of my flash drives, so I downloaded the netbook version (this is a laptop, but it has a fairly small screen) and got it installed on my 4 gig flash. But when I selected "Try Ubuntu" (or something like that) I kept getting messages that there wasn't enough room. So I tried the other flash, which is bigger - 8 gigs. Same message.

2) So I decided to just go ahead and install beside Windows (XP) on my hard drive. It's 120gigs, and the Windows side is using only 12 gigs, so there should be plenty of room.

3) According to instructions I found somewhere here, I ran Windows CHKDSK and then defragged. All went fine.

4) Booted from the flash drive and this time selected "Install beside Windows" (or something like that). Everything seemed to go OK - for a while. I got to the partition section and just chose 60 gigs, basically splitting the hard disk in half.

5) Got through the partition section and eventually got to a section asking for a computer name, user name, and password. Filled all of those in. There were two buttons at the bottom - "Back" and "Forward". Below that was a message saying "Ready when you are." But apparently it wasn't, because the "Forward" button never became active. When I clicked on the "Ready when you are" section it expanded into a black screen with some code in it, but no recognizable messages.

6) Things get confusing - or more confusing - after this. Since it seemed to be stuck, I tried rebooting, without the flash drive. Windows came up, and checking the size of the C: drive showed me that it was 59.x gigs, so the partition had indeed been made. but apparently the rest of the installation had failed.

7) Tried installing straight to hard drive with Unetbootin (from Windows, not the flash drive). Now, when I start the computer, I do get a choice of either Windows XP or Unetbootin. But when I select the latter, I get the Ubuntu logo and a series of dots under it that seem to indicate Ubuntu is loading, but it takes a really long time - longer than it takes XP to load. Then I get a blank desktop. From the way the colors are displayed t looks like there are two bars, one across the top and one on the left side. But there is nothing in them. The one on the left, when I "mouse over," shows blank (white) boxes; the one at the top, nothing.

So, really, I have two questions. First, Why do I have a blank desktop? And second, What can I do about it? How do I get this thing working so I can actually use it?

I did try a couple of searches here, and on Google, for "partial installation of Ubuntu" and its variations, but came up dry. If there is a thread that already addresses this problem, please feel free to direct me.

Thanks in advance for your help.

Meg

---

### Post by blazemore on 2011-01-01
The problem here is almost certainly an error in the download of the Ubuntu disk image.

The best course of action here is to download Ubuntu again, and when you boot into be sure to choose the option to verify files on the disk.

---

### Post by MargaretA on 2011-01-02
Actually, I think the downloaded file was verified the first time I tried to use it. But I just did it again using md5sum, and the hashes match.

I did just re-"burn" the downloaded file to the flash drive, and discovered when I booted with it that the applications and files *are* there - I just can't see them. The empty white boxes that appear when I move the mouse over the bar on the left side of the screen will open things when I click on them. I was able to open Firefox, play a game of Sudoku, and even connect to the internet - which itself was amazing because I have Cricket's wireless and setting up the modem is usually really complicated.

It seems that the desktop is just not displaying properly. I originally thought maybe it was an issue with the size of the flash; at one point, with an earlier "burn," I was getting "no more space available" messages. But in searching for "what size flash drive to use with Ubuntu" I found a discussion that basically said, since Ubuntu is 700 megs, a 1 gig flash would work, and in fact Ubuntu can't use more than 4 gigs. This flash is a 4-gig. So it should be OK.

But something is definitely not right; I can't see the icons or the fonts. It's like Ubuntu is playing "hide and seek" with me.

Has anyone had this problem before? If so, how did you solve it? I would like to use this operating system, and since I can't access the one I installed on the hard drive (that problem's in another thread here), if I can use the flash version at least I can start trying it out.

Meg

---

### Post by MargaretA on 2011-01-02
I think I have an answer to this question now.

A couple of people on Yahoo Answers suggested that the problem was with Unity and the ATI card on my computer. They suggested that I try the regular version of Ubuntu, which uses Gnome instead. After doing a Google search for "ubuntu netbook problems with ati radeon display" I found another thread on this forum, which is here:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=10309101#post10309101](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=10309101#post10309101)

The first post in that thread describes my exact problem - complete with images.

I thought I would do one final post here in case someone reads this and is wondering what happened with this thread. Now I'm going to do some more downloading.


Meg

---

