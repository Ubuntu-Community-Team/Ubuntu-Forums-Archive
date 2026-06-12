---
title: "Youtube issues... =["
date: 2009-07-02
forum: New to Ubuntu
---

### Post by CharlesWelsh on 2009-07-02
Youtube and other sites related will not allow me to properly watch videos. Every time I go to watch a movie, for some strange reason it either doesnt let me watch it, lags horribly (sound skips and freezes, video doesnt play yet audio does etc). Any suggestions? Thanks in a dvance...

---

### Post by philcamlin on 2009-07-02
reinstall flash and 
get both GStreamer plugins from synaptic :)

---

### Post by CharlesWelsh on 2009-07-02
I searched the Synaptics and I found one "GStreamer" and it is already installed. AND I reinstalled flash yeaterday...

---

### Post by philcamlin on 2009-07-02
in the top click all available applications

look at the screenshot to see where it is 

you should then see 3  

install it :)

---

### Post by CharlesWelsh on 2009-07-02
They are already installed. (And when you said 'synaptic i thought you meant the synaptic manager thing) Maybe i had a bad installation of Flash? Could you tell me how to uninstall and reinstall (Not sure how to do it. I am a 3 day young user of Ubuntu)) Thank you.

OR if it is another problem you may be aware of could you further assist me? Thanks in advance ;) -CJ

---

### Post by CharlesWelsh on 2009-07-02
i have adobe btw

---

### Post by philcamlin on 2009-07-02
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) 

go here and select deb for ubuntu 8.04+ 

and then once its done clck it and click reinstall package :popcorn::popcorn:

what happens after that ??

and you have all 3 GStreamer things installed in add remove?

---

### Post by CharlesWelsh on 2009-07-02
I pressed install. It ran through the process and I hit Re-Install. And it froze.

---

### Post by philcamlin on 2009-07-02
its obviously flash is the culprit.

try again and see what happens

---

### Post by CharlesWelsh on 2009-07-02
no luck. i used alt f4 and re did the process. went to youtube. still no luck.

---

### Post by philcamlin on 2009-07-02
sudo apt-get remove --purge flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
:popcorn:
then retart firefox

---

### Post by QIII on 2009-07-02
Are you using Compiz or Metacity as your window manager?

What type of video card/driver do you have?

---

### Post by CharlesWelsh on 2009-07-02
charles@Cjs-laptop:~$ sudo apt-get remove --purge flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.


I believe that is the issue. But i know i just did it =\

this is gonna be so much fun...

---

### Post by CharlesWelsh on 2009-07-02
> **QIII said:**
> Are you using Compiz or Metacity as your window manager?

What type of video card/driver do you have?

not sure. i believe the issue is... well read the other post... :(

---

### Post by philcamlin on 2009-07-02
sudo apt-get upgrade 

sudo apt-gett update

you have updates waiting that might fix it

---

### Post by CharlesWelsh on 2009-07-02
Still no luck. I updated. Then went into my file browser and installed the package. No luck. Did the thing where i remove and reinstall the package... still no luck. :(

---

### Post by philcamlin on 2009-07-02
try the beta firefox 

3.5 minefeild 

sudo apt-get *install firefox*-3.5

---

### Post by QIII on 2009-07-02
Could be a strange interaction between your video driver and your window manager.

If you have an ATI card and Compiz is your window manager, that may be your problem.

Please take a look at [http://ubuntuforums.org/showthread.php?t=1199020](http://ubuntuforums.org/showthread.php?t=1199020), post #9.

I have an ATI card, and I have to temporarily toggle to Metacity to get Flash to work satisfactorily.

---

### Post by CharlesWelsh on 2009-07-02
charles@Cjs-laptop:~$ sudo apt-get install firefox-3.5
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
charles@Cjs-laptop:~$ 

That is what came up. I'm sorry this is such a nuisance... and I GREATLY appreciate your efforts in helping me. Please, continue ;)

---

### Post by scrooge_74 on 2009-07-02
The real culprit is Flash 10, the non-free is ver 9 which works best in linux. I found that out a few days ago, seems the same happened when ver 7 came out, we had to use ver 6 since ver 7 gave problems same as with ver 10 now

---

### Post by philcamlin on 2009-07-02
reboot your pc then try again because something else is using root atm 

reboot fixes it  then sudo apt -get *install firefox*-3.5 :popcorn::popcorn:

---

### Post by scrooge_74 on 2009-07-02
> **CharlesWelsh said:**
> charles@Cjs-laptop:~$ sudo apt-get install firefox-3.5
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
charles@Cjs-laptop:~$ 

That is what came up. I'm sorry this is such a nuisance... and I GREATLY appreciate your efforts in helping me. Please, continue ;)

Do you also have synaptic open?

type ps -ax maybe you have apt still working in the background, in theory you can fix this without having to reboot

---

### Post by CharlesWelsh on 2009-07-02
Ummm.... GREAT news... The metacity thing worked. I have no idea what it is, what id does, or what it is for... But now I can watch my favorite videos on youtube ^^  Thanks much guys!!! -CJ:popcorn:

---

### Post by scrooge_74 on 2009-07-02
[http://en.wikipedia.org/wiki/Metacity](http://en.wikipedia.org/wiki/Metacity)

---

### Post by CharlesWelsh on 2009-07-02
and yes there was a synaptic... should i still upgrade to the new firefox?

---

### Post by scrooge_74 on 2009-07-02
Sure should be a bit faster, you may need to then manually link the pluggins (unless the version in the repos takes care of that)

You can also try Opera ;)

---

### Post by CharlesWelsh on 2009-07-02
Not... Working... Again... :(

---

### Post by scrooge_74 on 2009-07-02
what you did now? Which version of flash you have?

---

### Post by CharlesWelsh on 2009-07-02
10... All i did was watch a video about how to speed no$gba up and after that i went looking for another one and the same bs happened... -_-'

---

### Post by scrooge_74 on 2009-07-02
Try using ver 9 you should have a lot less problems

---

### Post by CharlesWelsh on 2009-07-02
> **scrooge_74 said:**
> Try using ver 9 you should have a lot less problems

i google searched version 9 and i couldnt find a way to download it. and if i were to just install it... would it properly do it? As in remove 10 and install 9?

Do i need the debugger versions as well?

---

### Post by philcamlin on 2009-07-02
yes you would purge 10 and install 9

---

### Post by scrooge_74 on 2009-07-02
Is in the repos under flashplugin-nonfree <---ver 9

and remove adobe-flashplugin <-- ver 10

You can do from command line

sudo apt-get install flashplugin-nonfree after doing a apt-get remove adobe-flashplugin

Or from synaptic remove one and install the other

---

### Post by CharlesWelsh on 2009-07-02
using the same functions you provided earlier?

---

### Post by philcamlin on 2009-07-02
> **scrooge_74 said:**
> Is in the repos under flashplugin-nonfree <---ver 9

and remove adobe-flashplugin <-- ver 10

You can do from command line

sudo apt-get install flashplugin-nonfree after doing a apt-get remove adobe-flashplugin

Or from synaptic remove one and install the other

purging would be better wouldent it ?  or is it the same

---

### Post by scrooge_74 on 2009-07-02
Well if I do a sudo apt-get remove adobe-flashplugin then ver 10 is gone

then I just need to install ver 9 and restart the browser

---

### Post by CharlesWelsh on 2009-07-02
> **philcamlin said:**
> purging would be better wouldent it ?  or is it the same

too late. i purged it... and the other guy told me 9 would be in the repos... I only found ver.10.

---

### Post by philcamlin on 2009-07-02
you cant get ver 9 anymore... 10 is better aparently 

reinstall it now and see if it works now :)

---

### Post by CharlesWelsh on 2009-07-02
I found a way to getflash 9... BUT i am not sure if its linux compatible. Or even how to install it if it is. heres the link so you can possibly tell me whether or not it will work on linux...

[http://kb2.adobe.com/cps/142/tn_14266.html](http://kb2.adobe.com/cps/142/tn_14266.html)

---

### Post by philcamlin on 2009-07-02
from the site 

These archived versions of Flash Player are available specifically for Flash developers who are assessing their sites from the perspective of users with different versions of Flash Player. For regular use, download the most current version of Flash Player, which is available from the [Flash Player Download Center]("http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash"). 


its a developer version :P 

thats not what you want :popcorn:

---

### Post by CharlesWelsh on 2009-07-02
OOOPS... lol umm... how about one of these?

[http://www.adobe.com/cfusion/search/index.cfm?loc=en_us&term=flash+player+9+linux&siteSection=cfusion%3Asearch](http://www.adobe.com/cfusion/search/index.cfm?loc=en_us&term=flash+player+9+linux&siteSection=cfusion%3Asearch)

---

### Post by CharlesWelsh on 2009-07-02
maybe?

[http://blogs.adobe.com/penguin.swf/2007/12/flash_player_9_update_3_final.html](http://blogs.adobe.com/penguin.swf/2007/12/flash_player_9_update_3_final.html)

---

### Post by philcamlin on 2009-07-02
ughh 

i can see how frusterating this is for you 

i cant find any deb file for ubuntu 

[http://kb2.adobe.com/cps/406/kb406791.html](http://kb2.adobe.com/cps/406/kb406791.html)

im not sure if that is for ubuntu but maybe scrooge 79 can answer 

did you install firefox beta?

*****

when you click the link 

this is where you get 

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---

### Post by CharlesWelsh on 2009-07-02
I appreciate your help. I can safely say I havent received help quite like this ever in this forum. And I'm hoping that with you & scroog79's help that we can get this figured out... Once again. Thank you. -CJ

---

### Post by CharlesWelsh on 2009-07-02
Okay here are those links... 
"http://blogs.adobe.com/penguin.swf/2007/12/flash_player_9_update_3_final.html"
thats what i think i need... i dunno though...

---

### Post by philcamlin on 2009-07-02
do you have compiz enabled?
try disabling that

sudo apt-get install ubuntu-restricted-extras 

 try that too sorry if it was already mentioned

---

### Post by philcamlin on 2009-07-02
> **CharlesWelsh said:**
> Okay here are those links... 
"http://blogs.adobe.com/penguin.swf/2007/12/flash_player_9_update_3_final.html"
thats what i think i need... i dunno though...


and when you click get it you get this 

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

flash 10 :(

---

### Post by scrooge_74 on 2009-07-03
Just remove ver 10 and install ver 9 from the repositories and you should be fine.

Lucky you I decided to log in tonight, but that is comming to and end, going to bed in a bit ;)

---

### Post by CharlesWelsh on 2009-07-03
Oh... this is all over my head. Noone else is having these problems? I did as you told... should i reinstall 10 now that i did the restricted thing? I am a noob to ALL of this. I have never used the terminal, never had these issues...

---

### Post by philcamlin on 2009-07-03
> **scrooge_74 said:**
> Just remove ver 10 and install ver 9 from the repositories and you should be fine.

Lucky you I decided to log in tonight, but that is comming to and end, going to bed in a bit ;)

yeah im tired too but ill stay up till i find out whats wrong

anyways i dont even have flash 9 in my repo :(

---

### Post by scrooge_74 on 2009-07-03
is the nonfree package ;)

---

### Post by philcamlin on 2009-07-03
> **CharlesWelsh said:**
> Oh... this is all over my head. Noone else is having these problems? I did as you told... should i reinstall 10 now that i did the restricted thing? I am a noob to ALL of this. I have never used the terminal, never had these issues...

ahah i had this issue with 8.10 my solution... reimnstall but im going to find out whats wrong 

i dont want you to reinstall :popcorn:

---

### Post by CharlesWelsh on 2009-07-03
Yeah, and all I can find online is the Developer version of 9... Maybe I should post a thread to see if anyone has any idea where i can get it... Scrooge went to bed...

---

### Post by philcamlin on 2009-07-03
you shouldent have to have version 9 

and what video card do you have?

---

### Post by CharlesWelsh on 2009-07-03
Umm... Everyonr just told me that 10 isnt very good with linux... And now you say i shouldnt need it? (Curious) And i dunno what video card i have...

---

### Post by philcamlin on 2009-07-03
10 is good but i dont see why you would need to downgrade

do you have a custom pc ?

or is it from liek a company liek dell?

what model is it?

then i can find the video card :D

because i think its your video card that needs a driver

---

### Post by scrooge_74 on 2009-07-03
I got one of those old HP nx6110, I was toying around the other day and I notice that after upgrading to ver 10 youtube stopped working, incidentally a friend called me that same morning about he not being able to watch youtube videos on his asus after he did an upgrade (paid upgrade I think he told me). Well that morning I had no clue, but since latter in the day I messed my flash by installing ver 10 and after reading around found about that same problem when ver 7 came out, I downgraded and that was the end of my problems.

And with that note I say good night is almost midnight and Im tired, take care ;)

---

### Post by philcamlin on 2009-07-03
> **scrooge_74 said:**
> I got one of those old HP nx6110, I was toying around the other day and I notice that after upgrading to ver 10 youtube stopped working, incidentally a friend called me that same morning about he not being able to watch youtube videos on his asus after he did an upgrade (paid upgrade I think he told me). Well that morning I had no clue, but since latter in the day I messed my flash by installing ver 10 and after reading around found about that same problem when ver 7 came out, I downgraded and that was the end of my problems.

And with that note I say good night is almost midnight and Im tired, take care ;)

hmm thats odd because upgrading from 9 to 10 
fixed my youtube issue

thats why im thinking video card now

---

### Post by CharlesWelsh on 2009-07-03
Toshiba Sttelite A15-S1292 lol 
and here is the screenshot prooving I DO NOT have the repo thing for flash 9 *cough Scrooge :p

**********

If it were my video card... would it have still played the video the one time? And whats weird.. Is i have no flash player installed... yet instead of youtube telling me to get one... it just acts up like normal. i wonder if i have a parallel installation of two flash players that may corrupt one another? Its just a theory... SMOKE BREAK ^^ Ill be back in a few minutes... thanks for your help my friend :)

---

### Post by philcamlin on 2009-07-03
can you give me a screenshot of you typing in mp3 

give me a better idea of what codecs are installed:popcorn:

and i know neither do i have the flash player 9 :P

---

### Post by CharlesWelsh on 2009-07-03
> **philcamlin said:**
> can you give me a screenshot of you typing in mp3 

give me a better idea of what codecs are installed:popcorn:

and i know neither do i have the flash player 9 :P

no prob... these and "movie player"

---

### Post by philcamlin on 2009-07-03
ok you clould be in working shape here but your not...
[http://tuxarena.blogspot.com/2009/07/how-to-install-firefox-35-in-ubuntu-904.html](http://tuxarena.blogspot.com/2009/07/how-to-install-firefox-35-in-ubuntu-904.html)

try that that should help !!!!!!!!

this is really frusterating :mad::mad::mad:

---

### Post by CharlesWelsh on 2009-07-03
Okay... from what i was reading that web browser has bad reviews... you sure i should do that??? *worried

---

### Post by philcamlin on 2009-07-03
AH!

i never thought of using opera until now 

[http://www.opera.com/](http://www.opera.com/)

i used it back in the day but im going ot try it right now too :D

im out of ideas i think you should try it and its not in beta :)

---

### Post by CharlesWelsh on 2009-07-03
thats a no go. it wouldnt work...

---

### Post by CharlesWelsh on 2009-07-03
never heard of opera. but it is VERY appealing ^^ ill give it a shot

---

### Post by philcamlin on 2009-07-03
ok its one of my last ideas :) 

hope it works !!!

---

### Post by CharlesWelsh on 2009-07-03
still no youtube... wtf

---

### Post by CharlesWelsh on 2009-07-03
What were the commands for purging and reinstalling flash?

---

### Post by philcamlin on 2009-07-03
no youtube or laggggg :(

---

### Post by CharlesWelsh on 2009-07-03
no youtube...

---

### Post by CharlesWelsh on 2009-07-03
would shockwave flash player interfere with adobe? if so maybe thats the problem...

---

### Post by philcamlin on 2009-07-03
can i get a screenshot... 

sorry for all the requests :P

maybe. try removing it :)

---

### Post by CharlesWelsh on 2009-07-03
screenshot of what? lol

---

### Post by philcamlin on 2009-07-03
ah nevermind :P

ive gone through 130 pages of google looking for a solution :P
cant find anything :(

---

### Post by philcamlin on 2009-07-03
what does opera saywhen you want to watch a youtue video :popcorn:

WAIT!

what do you mean you have adobe :P flash player is by adobe?

---

### Post by CharlesWelsh on 2009-07-03
yeah...

---

### Post by philcamlin on 2009-07-03
do you have java installed?

---

### Post by CharlesWelsh on 2009-07-03
yep. i needed it to play runescape lol

---

### Post by philcamlin on 2009-07-03
ok i think i have your answer then 

java slows things down to a crawl 

try uninstalling it for like 5 min annd try and watch a youtube video 

and can i ask how old you are :P

---

### Post by CharlesWelsh on 2009-07-03
17 my friend... and how do i do that?

the runtime and plugin?

---

### Post by philcamlin on 2009-07-03
type in java in add/remove and it should be the first one there

---

### Post by CharlesWelsh on 2009-07-03
lol i got two... just want to be sure

---

### Post by philcamlin on 2009-07-03
remove both 6.0 plugin and runtime

after...

and get  the icetdea java plugin after its waaay batter and both open JDK java 6 runtime and webstart

---

### Post by philcamlin on 2009-07-03
that should solve all your problems!!

---

### Post by CharlesWelsh on 2009-07-03
okay. i will have to try this tomorrow. i need to go to sleep. doc appt. i will im you with the results. once again thank you soooooo much. hopefully runescape will still work...

---

### Post by philcamlin on 2009-07-03
yes i just went to the site and it loaded :)

no problem :popcorn::popcorn:

pm me if it does / doesnt

---

### Post by scrooge_74 on 2009-07-03
Just so you know that pic is not exactly Synaptic, Synaptic is in System>Admin>Synaptic

If you add all the other repositories you get a lot more programs not just those in the add/remove software

---

### Post by milamoto3 on 2009-07-03
Hi,

Im running Ubuntu 8.04 LTS 2.6.24-24-generic x86_64 GNU/Linux.

Downloaded Adobe Flash from [http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb](http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb))

But it only has 32bit version available.

Anyone know how to pull off a McGuyver ?

please could you let me know.

Thanx

---

### Post by scrooge_74 on 2009-07-03
> **CharlesWelsh said:**
> okay. i will have to try this tomorrow. i need to go to sleep. doc appt. i will im you with the results. once again thank you soooooo much. hopefully runescape will still work...

Ubuntu 7.10 (Gutsy Gibbon) and 8.04 (Hardy Heron)

This method will install the latest flashplayer from the Ubuntu repositories, for Firefox, Konqueror, Mozilla, Epiphany and other browsers. 

Enable the Multiverse repository if you have not yet done so. 

Install the package flashplugin-nonfree. 
Restart your web browser. Flash should now work. 

After installing flashplugin-nonfree, sound in Flash will not work. To fix this, install libflashsupport.

As for 64 bit flash did you check in Synaptic? I think there should be a version there. This [news]("http://www.linuxfordevices.com/c/a/News/Adobe-unleashes-64bit-Flash/") articles says there is a version.

---

### Post by philcamlin on 2009-07-03
> **milamoto3 said:**
> Hi,

Im running Ubuntu 8.04 LTS 2.6.24-24-generic x86_64 GNU/Linux.

Downloaded Adobe Flash from [http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.deb"))

But it only has 32bit version available.

Anyone know how to pull off a McGuyver ?

please could you let me know.

Thanx

here you go [http://www.dailygyan.com/2008/11/install-64-bit-flash-player-plugin-for.html:popcorn::popcorn:](http://www.dailygyan.com/2008/11/install-64-bit-flash-player-plugin-for.html:popcorn::popcorn:)

---

### Post by CharlesWelsh on 2009-07-03
okay. this is what i have... after the instructions you gave me... take a look and see if i got it right...

---

### Post by philcamlin on 2009-07-03
yes you have the right java installed

are you 32 or 64 bit?

---

### Post by CharlesWelsh on 2009-07-03
32.

---

### Post by philcamlin on 2009-07-03
sudo apt-get purge firefox

 sudo apt-get install firefox 

im totally out of ideas after that 

that cleans out firefox and then reinstalls it fresh

---

### Post by raafaell on 2009-07-03
you can also try to install the > flashplugin-nonfree try ```
sudo apt-get install flashplugin-nonfree
```

---

### Post by CharlesWelsh on 2009-07-03
this is really pizzin me off.. It still does not work. Neither does Opera... I dont get it. I;m beginning to think i have something installed i shouldnt...

---

### Post by philcamlin on 2009-07-03
> **raafaell said:**
> you can also try to install the  try ```
sudo apt-get install flashplugin-nonfree
```

he tried that already liek 8 times :P

everybode keeps saying get that byt it doesnt work :(

---

### Post by CharlesWelsh on 2009-07-03
how do i import certificates here? if i need to... lol i dont even know what the certificate is used for. But how did we get on Java for youtube? Is this a flash plugin?

---

### Post by philcamlin on 2009-07-03
> **CharlesWelsh said:**
> this is really pizzin me off.. It still does not work. Neither does Opera... I dont get it. I;m beginning to think i have something installed i shouldnt...

its not that its your missing something you should have 

java is there and its the right one. 

do yuo have the icedtea java plugin?

you have flash the correct version 

i know how you feel ive had those problems with windows before

java is for your runescape and vvideo

---

### Post by raafaell on 2009-07-03
> **philcamlin said:**
> its not that its your missing something you should have 

java is there and its the right one. 

do yuo have the icedtea java plugin?

you have flash the correct version 

i know how you feel ive had those problems with windows before

java is for your runescape and vvideo

I don't have java installed, and i can watch and play flash games, do you really need java for playing .flv videos?

---

### Post by philcamlin on 2009-07-03
> **raafaell said:**
> I don't have java installed, and i can watch and play flash games, do you really need java for playing .flv videos?

its for runescape thta he plays 

runescape needs java i used to play it when i ws 11 :P

---

### Post by raafaell on 2009-07-03
> **philcamlin said:**
> its for runescape thta he plays 

runescape needs java i used to play it when i ws 11 :P

oh, i see. ;)

---

### Post by CharlesWelsh on 2009-07-03
this stufff... whhats the terminal thing for installing and purging flash?

---

### Post by CharlesWelsh on 2009-07-03
And personally... ihate the game... But, since my emulators arent working properly.... anyways... I dont understand why this has to be such a hassle...

---

### Post by CharlesWelsh on 2009-07-03
Its just for some reason youtube and videos do not want to help. I wish i could consult an expert or something... I dont know what to do and youve tried just about everything... Its mindboggling...

---

### Post by CharlesWelsh on 2009-07-03
okay well i need to take  break. im getting very aggitated. I have an idea!!!!!! ^^ Maybe running Chrome in wine?

---

### Post by scrooge_74 on 2009-07-03
Why you want to run Chrome in wine? There is a version already for linux. You really need to drop the Windows mind set, and check back what we have being telling you already, which I feel you havent really follow.

Search the forum for the restricted stuff in here so you can download an install all the stuff needed to get your Browsers working properly

---

### Post by CharlesWelsh on 2009-07-03
I can see why you are a scrooge. I; unlike you, do not know how to find these things you guys do know how to find. Thats why I'm in the BEGINNERS forum. Thanks anyways, but i have no idea as to what you are talking about...

---

### Post by CharlesWelsh on 2009-07-03
So, I figured I'd expand my search resources a little bit and maybe some of you can help. It would be greatly appreciated. If you are interested in helping;

[http://ubuntuforums.org/showthread.php?t=1203001&highlight=youtube](http://ubuntuforums.org/showthread.php?t=1203001&highlight=youtube)

See what routes we have taken, maybe you might be able to help me. 
Thanks in advance...
-CJ

---

### Post by scrooge_74 on 2009-07-03
We are at post #110 and I feel you haven't beeing following directions.

We tell you go use Synaptic, and you go use add/remove programs. We tell you flash is in the repositories and you want to download it from adobe. 

Now you want to use Chrome using wine, when there is no need and wine will only further complicate you at this point.

First question, did you remove Flash 10?
Second question, did you installed Flahs 9?

There is a search tool in the forum or you can google.com/linux for stuff that is the way I find things.

With little effor you can go to the main forum page and go for Multimedia & Video and you will find pretty good instructions for most of the issues you have right now.

[Here is the link]("http://ubuntuforums.org/showthread.php?t=766683")

You need to start from scratch and follow the instructions to the letter and do not go wondering in any other direction until you get one set of issues resolve and get a hang of it.

Is not hard is just a different way of doing things

---

### Post by halitech on 2009-07-03
1 thing you mention back on page 2 or 3 (hard to believe a thread has gone this long about youtube :) ) is that you switched to Metacity. Have you tried doing that again?

also, knowing what video card you have may help out some as well. Open a terminal and post the results of ```
lspci
```

---

### Post by CharlesWelsh on 2009-07-03
Answer to the first question. I did. But then I got a PM telling me to reinstall it. SECONDLY... I do not see the flash player 9. I honestly dont. I can send you a screenshot to prove it. I understand it is frustrating... It is for me to. I understand I may not be following instructions... And I'm sorry for that. I will start from scratch.

---

### Post by CharlesWelsh on 2009-07-03
> **halitech said:**
> 1 thing you mention back on page 2 or 3 (hard to believe a thread has gone this long about youtube :) ) is that you switched to Metacity. Have you tried doing that again?

also, knowing what video card you have may help out some as well. Open a terminal and post the results of ```
lspci
```

I'm still in metacity...
Here you go...

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
01:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)
02:00.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

---

### Post by scrooge_74 on 2009-07-03
Intel video card, should not be having problems there, my money is still with flash 10 giving problems.

Go to System> Software origin and enable the other repositories I think no one told you to do that and I think flashpluging-nonfree is in those

It wont hurt you to follow the multimedia guide first, there is a lot of stuff you need to install from there just follow those instructions

---

### Post by CharlesWelsh on 2009-07-03
> **scrooge_74 said:**
> Intel video card, should not be having problems there, my money is still with flash 10 giving problems.

Go to System> Software origin and enable the other repositories I think no one told you to do that and I think flashpluging-nonfree is in those

It wont hurt you to follow the multimedia guide first, there is a lot of stuff you need to install from there just follow those instructions

I dont see "Software origin" Under system...

---

### Post by halitech on 2009-07-03
> **scrooge_74 said:**
> Intel video card, should not be having problems there, my money is still with flash 10 giving problems.

Go to System> Software origin and enable the other repositories I think no one told you to do that and I think flashpluging-nonfree is in those

It wont hurt you to follow the multimedia guide first, there is a lot of stuff you need to install from there just follow those instructions

not a problem so they have a bug posted on launchpad
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/355761](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/355761)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/314928](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/314928)

Here is some info on "fixing" the issue
[http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html)

---

### Post by CharlesWelsh on 2009-07-03
all those codes... stuff like that... how do i do them?

EG. this is what i get 

charles@Cjs-laptop:~$ $ wget -c [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/linux-headers-2.6.30-020630rc2-generic_2.6.30-020630rc2_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/linux-headers-2.6.30-020630rc2-generic_2.6.30-020630rc2_i386.deb) [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/linux-headers-2.6.30-020630rc2_2.6.30-020630rc2_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/linux-headers-2.6.30-020630rc2_2.6.30-020630rc2_all.deb) [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/linux-image-2.6.30-020630rc2-generic_2.6.30-020630rc2_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/linux-image-2.6.30-020630rc2-generic_2.6.30-020630rc2_i386.deb) [http://ftp.us.debian.org/debian/pool/main/libd/libdrm/libdrm2_2.4.9-1_i386.deb](http://ftp.us.debian.org/debian/pool/main/libd/libdrm/libdrm2_2.4.9-1_i386.deb) [http://ftp.us.debian.org/debian/pool/main/libd/libdrm/libdrm-intel1_2.4.9-1_i386.deb](http://ftp.us.debian.org/debian/pool/main/libd/libdrm/libdrm-intel1_2.4.9-1_i386.deb) [http://http.us.debian.org/debian/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.7.0-1_i386.deb](http://http.us.debian.org/debian/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.7.0-1_i386.deb)

---

### Post by scrooge_74 on 2009-07-03
At this point you have to follow the instructions to the letter, read them again and use the sections that go for the version of Ubuntu you are using

---

### Post by CharlesWelsh on 2009-07-03
okay... I run this command... 
gksudo gedit /etc/X11/xorg.conf
and this is what I get...
...
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
...

And this is what it should say...

Section "Device"
Identifier    "Configured Video Device"
Option        "AccelMethod"            "uxa"
**Option        "Tiling"            "false"**
EndSection

WTF?

---

### Post by CharlesWelsh on 2009-07-03
Wahooooooo!!!! Its PERFECT!!!!!!! THANK YOU SCROOGE!!! (Even though you acted like a d-bag) I'm so excited ^^ I need to learn how to use the terminal efficiently. Thanks guys!!!

---

