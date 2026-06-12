---
title: "How to change Octoshape stream to VLC from Mplayer (default)"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by DesiArnez6 on 2010-06-17
After working on this about 8 hours straight, I need help

I am trying to watch the 2008 Eurovision First Semi-Final at: octoshape://ond.octoshape.com/ESC/ESC_semi1_700;streamtype=vod/ond

It opens in mplayer and randomly after awhile, stops and closes, which is frustrating if you are 15 minutes into it and have to keep repeating from the beginning, I think VLC was the solution I used years ago on my last computer?

So, I read that I'm supposed to modify the setup.xml, I have modified it in nearly every way possible, please help me, so that maybe I can watch the whole thing. ;)

---

### Post by DesiArnez6 on 2010-06-17
This thread is similar to my problem 

[http://ubuntuforums.org/showthread.php?t=1511942](http://ubuntuforums.org/showthread.php?t=1511942)

In fact, i ran into almost the same setup.xml as jrib ...And can't get it to work, But only barely with mplayer, i have to re install anyways to atleast get something on mplayer since that wont work either even tho i had an original back-up of the xml file

Does anyone know how to create this  "new" setup.xml code to use vlc? Ill take any player at this point.

---

### Post by mc4man on 2010-06-17
It's been a while since I used Octoshape, not on this install - can you post the first several lines of your xml in a codebox

( as I remember it's not that hard to set to vlc.

The thread you linked to is this thread...

Edit:
went ahead and installed - added this to config line to use vlc - works fine
```
PlayerExec="vlc $url"
```
So for instance my line looks like this now after using on something ( I added it after EulaAccepted="true" <space> PlayerExec="vlc $url" <space>

```
<config EulaAccepted="true" EulaId="0905190.en" EulaMethod="installer" Language="en"
    PlayerExec="vlc $url" TempID="Ehenysk_Detvak_07838818"/>
```

---

### Post by DesiArnez6 on 2010-06-18
Thx mc4man, just wook up at the computer :p (Its now 4am) Thanks for your post! 

Just in case: Additional info: I run jaunty

First I had the original system.xml file that used mplayer, with constant crashing. For some reason when I'd repaste the original code  after fiddling around withh all the possibilites like /usr/bin/vlc or just vlc, or code with java. So it no longer worked so i had to re-execute the bin file and I'd be back to square 1. 

The new "official" directions from Octoshape site at: [http://www.octoshape.com/?page=get_octo/faq#62cdcc](http://www.octoshape.com/?page=get_octo/faq#62cdcc)
^So you can see their vagueness, they recommend "... add the PlayerExec attribute as shown below.

<config EulaAccepted="true” PlayerExec="vlc $url">

This example shows how to use vlc as the player. For simplicity many values have been removed in this example."

Nothing, just errors, I posted below what was there, also tried to get rid of the original and just post from their example....Nothing, no matter what I did it didn't work.

******** Solution time :) :) :) ********

I found this little bit, the Archivre of the OLD instructions here:

[http://archive.octoshape.com/faq/faq.asp?faqtype=Linux](http://archive.octoshape.com/faq/faq.asp?faqtype=Linux)

Which basically says: "You can manually set your player in the setup.xml file, like this:

<e PlayerExec="someotherplayer $url" /> "
Well...



So, I erased all text from setup.xml and I tried this:


<e PlayerExec="vlc $url" /> 


Unbelievable, that was it! I did see that my setup.xml file changed on its own by adding to the end. It now reads:

<e PlayerExec="vlc $url" TempID="Bejert_Daspuvgel_0110072"/>


Octoshape needs to use their archive of their FAQ , becaause the new instructions just sent me in the wrong directions. I THOUGHT it was easier the last time,... now I know why :)

I sincerely hope this helps someone out there. I came across several similar posts and threads thoughout the web with frustated users just not getting sucess at this problem.


Victory!!!!!! :) (And I can even pause and continue, and no crashing :)  )

---

### Post by ozdemir on 2012-12-11
Hi.  i tried it successfully but warning message was showed:  ```
Status: Reading configuration  Status: Registering plugins.  Status: Ready to play Status:  Playing Status: Ready to play  Info  : You do not have permission to view this stream.  
```  i have got this stream membership and how could i do watching this?  Thanks.

---

### Post by overdrank on 2012-12-11
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

