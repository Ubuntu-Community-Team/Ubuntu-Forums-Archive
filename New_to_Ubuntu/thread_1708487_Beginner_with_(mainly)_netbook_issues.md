---
title: "Beginner with (mainly) netbook issues"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by ayupmiduck on 2011-03-16
Hello, this is my first time post.

I have been using Ubuntu  exclusively for about a week on my desktop ( by accident. I wanted to  duel boot XP but ended up dedicating my whole partition to Ubuntu...  doh)

Good news is I don't miss Windows. Ubuntu does everything I want and need from a PC from what I can see.

in  fact i have been so impressed that I have installed 10.10 on my Samsung  N145 netbook. (Desktop version, I was not so impressed by NBR) and I  even managed to duel boot with Windows 7 starter GO ME ^^

However,  I must admit that I have become so frustrated with certain things that I  cannot figure out (terminal has almost brought me to tears.)

I require some assistance with a few things and would be grateful for any help given. 

Some questions are relevant to both my desktop and netbook PC and some are just in regards to the netbook. Here we go...

My  main issues are with my netbook (Samsung N145) There is a site, which  has helped me with some of my issues, but then I have got stuck with the  terminal.

I am trying to follow the instruction found on 
[http://twistedpairdevelopment.wordpress.com/2010/11/16/installing-ubuntu-on-a-samsung-n145-and-possibly-others/](http://twistedpairdevelopment.wordpress.com/2010/11/16/installing-ubuntu-on-a-samsung-n145-and-possibly-others/)

I  have got as far as completing the section on brightness keys freezing  keyboard. Everything beyond that is not working. Particularly the  suspend/resume instruction

**[COLOR=Blue]Suspend / Resume[/COLOR]**

 [COLOR=Blue]**Note:** This should normally work on its own, but a  regression in the 2.6.3x Linux kernels requires us to use the existing  2.6.32 kernels from Lucid Lynx, in addition to the following steps,  which is described at the end of this section. Bug report [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/640100?comments=all").[/COLOR]
 [COLOR=Blue]Suspend and resume causes the system to freeze on resume (some  activity, but the screen never powers back on). There are also issues  with wireless networks coming in and out of range when roaming that  cause the system to continually lock itself and eventually freeze.[/COLOR]
 [COLOR=Blue]This modifies the ACPI flags set in Grub (from [here]("http://ubuntuforums.org/showpost.php?p=9992908&postcount=33")).  This resolves all freezing issues with suspend / resume and wireless  networks coming into and out of range when roaming (I ran my laptop on  the tram today with no issue!).[/COLOR]
 [COLOR=Blue]1.At the console, type the following:[/COLOR][INDENT] [COLOR=Blue]sudo vi /etc/default/grub[/COLOR]
 [/INDENT][COLOR=Blue]2.change the following line[/COLOR][INDENT] [COLOR=Blue]GRUB_CMDLINE_LINUX=”"[/COLOR]
 [/INDENT][COLOR=Blue]to[/COLOR][INDENT] [COLOR=Blue]GRUB_CMDLINE_LINUX=”acpi_sleep=nonvs”[/COLOR]
 [/INDENT][COLOR=Blue]3. Type the following[/COLOR][INDENT] [COLOR=Blue]sudo update-grub[/COLOR]
 [COLOR=Blue]sudo reboot[/COLOR]


[LEFT][COLOR=Blue][COLOR=Black]I have managed to change the line, but then I type[/COLOR][/COLOR]


[COLOR=Black]sudo update-grub (enter)[/COLOR]
[COLOR=Blue][COLOR=Black]sudo reboot (enter)[/COLOR][/COLOR]


[COLOR=Blue][COLOR=Black]Nothing happens? 
[/COLOR][/COLOR]


[COLOR=Blue][COLOR=Black]If  I suspend or shut my laptop, I get a blank black screen, so it is vital  I get this fixed. Unfortunatley I dont seem to be getting anywhere.[/COLOR][/COLOR]


[COLOR=Blue][COLOR=Black]Also the following instruction does not seem to get me anywhere[/COLOR][/COLOR]

[/LEFT]
**[COLOR=Blue]Vi keys[/COLOR]**

 [COLOR=Blue]The Vi keys can be fixed by doing the following (from [here]("http://ubuntuforums.org/showpost.php?p=1677009&postcount=3")):[/COLOR]
 [COLOR=Blue]1. Type the following:[/COLOR][INDENT] [COLOR=Blue]touch ~/.vimrc[/COLOR]
 [COLOR=Blue]vi ~/.vimrc[/COLOR]
 [/INDENT][COLOR=Blue]2. add the line[/COLOR][INDENT] [COLOR=Blue]set nocompatible[/COLOR]


[COLOR=Blue][COLOR=Black]I  type the first 2 lines but then try and add the third line and "no"  does not show, only compatible will type and then if I press enter...  nothing...[/COLOR][/COLOR]
[COLOR=Black]
[/COLOR]
[COLOR=Blue][COLOR=Black]I  would be so grateful for any assistance provided for the above. I would  like to complete all the stages of the above url but am really  struggling.[/COLOR][/COLOR]


[COLOR=Red]
[/COLOR]
[COLOR=Blue][COLOR=Red]The below, I could probably work out myself, but if anyone has the time and patience to assist, it'd be great.[/COLOR]
[/COLOR]
 [/INDENT][/INDENT]1. What's the difference between  the key ring password and a normal password? and how can i make it so  that my PC does not ask me for a key ring password on start up? I only  want a password to exist for installations and system amendments. Also  how do I change such a password

2. On the evolution client for  email/organisation, am I able to set up multiple users? from one desktop  login? If so, how? Am I able to set passwords for these accounts?

3.  On the start up applications, which programmes are vital for the system  to run? and which can be removed. Does doing such speed up PC start up  performance as with Windows?

4. On the net book remix, when I  opened folder, the background was translucent and I could see my desktop  background. I liked this feature, how do I have the same effect on the  desktop 10.10 version?

5. Can I have different wallpapers for the 4 worktops available? If so, how is it done?

6.  When using the 'cube effect' on my desktop I have managed to change the  image on the top of the cube, but cant see an option to change the  picture on the underside. Any suggestions?

7. Any suggestions for a decent music player? My main requirement is sound quality and cover art 'eye candy'


Sorry for my huge first post and for having a whine.


Much love
^^

---

### Post by cariboo on 2011-03-17
The version you are using, is more or less and orphan, as there is a new version of Unity set to be released at the end of April. The problems you are suffering from will not be fixed, as no-one is working on it any more. Sorry to be so harsh, but UNE 10.10 didn't work well for most people, and was decided that development should start all over again.

If you can hold on until the release of Natty Narwhal (11.04) April 28, 2011, most of your problems should be solved.

---

