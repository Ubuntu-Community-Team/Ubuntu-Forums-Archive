---
title: "Gaydar"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by shleena on 2009-02-27
hi... im new to ubuntu, i have switched from windows, everything is working perfectly but im having trouble accessing the chat on [www.gaydar.co.uk](www.gaydar.co.uk)

i have the latest java and youtube works, but when i enter, there is a diagonal line on chat and i cannot view profiles, i have allowed popups for the site but even the emoticons seem... buggy. anyone had the same problem and does anyone have a fix? ubuntu 8.10 if you need me to print out some terminal info please tell me what to put in lol thanks everyone :) im using an acer aspire 1640z with 1gig ram and intel centrino processor

---

### Post by binbash on 2009-02-27
are you using sun's java?paste the output of : 

sudo update-java-alternatives -l

---

### Post by shleena on 2009-02-27
java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-6-sun 63 /usr/lib/jvm/java-6-sun

also it seems that when i enter chat my processor is always at 100% and when its not it goes down to about 15%

---

### Post by binbash on 2009-02-27
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk sun-java6-plugin

then after this : 

sudo update-java-alternatives -s java-6-sun

Restart your browser and report if the issue continues or not.

---

### Post by shleena on 2009-02-28
wow, well that definitely seems to have sorted it for the time being, got a nice window that is "recognized" and it all works as it should be, thanks man! hehe love ubuntu. thanks again!

---

### Post by binbash on 2009-02-28
you are welcome

---

### Post by gritsandeggs on 2010-08-23
I'm having the same issue w/ Gaydar's Java chat on my new laptop. It works fine on my five year old desktop, ironically. I read the answer to your issue, but it makes no sense to me.  (below) If you have the time, will you just tell me what to download, where I can get it & how to configure it. I don't know what 'sudo' is and I can't seem to find a file 'openjdk'. I just want to use Gaydar chat. I'm not a programmer or computer whiz. Thanks

java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-6-sun 63 /usr/lib/jvm/java-6-sun
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk sun-java6-plugin
sudo update-java-alternatives -s java-6-sun

---

### Post by opto09 on 2010-08-23
This is quite an old post but I assume that the fix still works. "sudo" is just Ubuntu's way of saying "run with administrative privileges" i.e. you can install stuff on your computer. "apt-get" is the package manager program that will grab the package that you want, in this case "sun-java6-bin", "sun-java6-jre" etc. and install them. It will so this automatically so assuming the above solution still works all you need to do is:

1. Open Terminal (Applications-> Accessories-> Terminal
2. Type in the code from above:

> 
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk sun-java6-plugin

then after this : 

sudo update-java-alternatives -s java-6-sun

3. Restart your browser and see if it works.

Hope this helps.

---

### Post by sleepsfuriously on 2010-10-09
Hey guys, I'm facing a slightly different problem. When I try to load the chat, a new window opens put stays permanently "connecting".

Thanks in advance for any help.

---

### Post by numan2008 on 2010-10-27
hi,
iam having the exact same problem, how did you fix it?

---

### Post by no2498 on 2010-10-27
any time you use sudo you need to type in your pass word

sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk sun-java6-plugin
click enter now it ask for your pass word you do not see it but it is ok click enter

then after this :  should not ask for pass word

sudo update-java-alternatives -s java-6-sun

---

### Post by ericdn on 2010-10-27
> **binbash said:**
> sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk sun-java6-plugin

then after this : 

sudo update-java-alternatives -s java-6-sun

Restart your browser and report if the issue continues or not.

I've been looking for an easy way to install Java, since the download packet from the Java webpage is... well... beyond my capabilities.  Just by randomly reading the forums you solved my problem!  Thank you very, very much!! :)

---

### Post by W1tch on 2010-11-14
Hello, new to ubuntu and not particularly savy ..:( ...I too have the same problem and the above fixes didnt work - but I am using Luccid, would that make a difference. Could anyone help ?

---

### Post by teddansonswig on 2010-12-21
same here ... java is uptodate, wont load in any browser!
thanks to anyone who helps!

---

### Post by snoggeruk on 2011-01-16
I'm not a techie either but have been told that Gaydar now uses Flash.

I use Lucid and periodically uninstal and then reinstall the flashplayer via Synaptic Package Manager and sometimes it seems to cure the problem for a while.   However, the problem is intermitent, i.e. sometimes there is no problem for hours, other times within a few minutes of opening all Gaydar chat windows, all hang/freeze.  It appears to be a greater problem during the daytime - yeah don't ask me why.  I have also been told that Virgin (my ISP) has acknowledged problems with Gaydar, although I don't have problems when accessing gaydar using windows 7, which leads me to believe this is an Ubuntu/Adobe problem rather than Virgin.

Probably wont help the previous posts, but hopefully will provoke some response from those more technical than me.

---

### Post by [Snc] on 2011-01-16
> **snoggeruk said:**
> I'm not a techie either but have been told that Gaydar now uses Flash.

I use Lucid and periodically uninstal and then reinstall the flashplayer via Synaptic Package Manager and sometimes it seems to cure the problem for a while.   However, the problem is intermitent, i.e. sometimes there is no problem for hours, other times within a few minutes of opening all Gaydar chat windows, all hang/freeze.  It appears to be a greater problem during the daytime - yeah don't ask me why.  I have also been told that Virgin (my ISP) has acknowledged problems with Gaydar, although I don't have problems when accessing gaydar using windows 7, which leads me to believe this is an Ubuntu/Adobe problem rather than Virgin.

Probably wont help the previous posts, but hopefully will provoke some response from those more technical than me.

well if its flash, and you use firefox, than here is the solution:

Flash-Aid - [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by teddansonswig on 2011-02-16
thanks for the help mate,
unfortunately no luck still on mozilla
sent this to their support


hello andre 
 
using both chrome(the original open source program, not google chrome )

and firefox 3.6.13, with Flash-Aid - [https://addons.mozilla.org/en-US/fir...don/flash-aid/](https://addons.mozilla.org/en-US/fir...don/flash-aid/) , 

using  10,2,152,27 Flash ([http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/))

32 bit

OS: ubuntu 10.04

broadband wireless

SP: Eircom (Republic of Ireland)

no firewall
no antivirus

the problem: never being able to run gaydar chat, the pop up window opens and in the status bar : connecting to gaydar.co.uk
havent been able to use chat on ubuntu ever, and others having this problem too
[http://ubuntuforums.org/showthread.php?t=1082326&highlight=gaydar](http://ubuntuforums.org/showthread.php?t=1082326&highlight=gaydar)

the only error message of sorts i got was 
LOADING_CONFIG
INITIALISED
LOADING_POLICY
CONNECTING

THANKS!!

---

