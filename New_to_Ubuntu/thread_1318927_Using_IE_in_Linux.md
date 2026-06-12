---
title: "Using IE in Linux"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by mcooke1 on 2009-11-08
I am trying to make a total break from using Windows on my Computers and have been working on this for some time, and using linux I have found alternatives for everything I use my computers for other than one small detail. I am on satellite broadband and if it goes down I need to access the modem and can only do this with Internet Explorer. I know I can use IE with Ubuntu and I know how but does the use of it on the internet create security issues that do not exist without it.

---

### Post by Dark_Stang on 2009-11-08
Using IE in Linux would pose a very minor risk, if any risk at all. The only thing I can think of is you may get a browser hijacker on it, but that would be easily fixed. If you need it you can run it through WINE, but I wouldn't bother using it unless you absolutely had to. IE is cumbersome and slow, stick with Firefox or Opera or Epiphany.

---

### Post by sliketymo on 2009-11-08
Do you mean use your dial-up modem for back up? What browser you use shouldn't make a difference .

---

### Post by phrostbyte on 2009-11-08
It is possible to run [IE on Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page"), although *I really* do not recommend so for web browsing.

---

### Post by Cybie257 on 2009-11-08
> **sliketymo said:**
> Do you mean use your dial-up modem for back up? What browser you use shouldn't make a difference .

He's referring to a satellite modem connected to a satellite dish and, yes, they can be picky about the browser, just as some email systems will only allow IE browsers to access them properly. 

-Cybie

---

### Post by SunnyRabbiera on 2009-11-08
Are you getting net under Ubuntu?
Are you even on Ubuntu right now?
Just asking, as if you are getting net in ubuntu i say to hell with IE, and to your ISP for forcing IE on people

---

### Post by Cybie257 on 2009-11-08
> **mcooke1 said:**
> I am trying to make a total break from using Windows on my Computers and have been working on this for some time, and using linux I have found alternatives for everything I use my computers for other than one small detail. I am on satellite broadband and if it goes down I need to access the modem and can only do this with Internet Explorer. I know I can use IE with Ubuntu and I know how but does the use of it on the internet create security issues that do not exist without it.

Have you thought about the idea of installed VirtualBox and having and XP installation within it to run certain things. Regardless of how 'non-windows' us Linux users want to become, there will always be a time when we have to use something in Windows. Of course, this all depends on the technical aspects of what we do with our computers. :)

-Cybie

---

### Post by mcooke1 on 2009-11-08
> **sliketymo said:**
> What browser you use has no bearing on accessing the internet via a modem.Some sites apparently require IE to be able to use all the features of that particular site.The security of one browser over another is yet to be determined.
 
Thanks for the reply, but currently I use Firefox, Opera, Seamonkey and sometimes Chrome but none of these can be used for connecting to the modem for diagnostic purposes if there is a problem with the connection. I am concerned about the security issues I hear about that exist with IE.

---

### Post by SunnyRabbiera on 2009-11-08
> **mcooke1 said:**
> Thanks for the reply, but currently I use Firefox, Opera, Seamonkey and sometimes Chrome but none of these can be used for connecting to the modem for diagnostic purposes if there is a problem with the connection. I am concerned about the security issues I hear about that exist with IE.

What modem model is this anyhow?
Is it some generic, does it have a brand?
Certainly there must be a diagnostic you can use without IE.
Who is your provider?

---

### Post by jcris on 2009-11-08
The very best way to use IE in Ubuntu is to install the stable wine in your repo, and run 

wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
in a terminal then run

sh winetricks ie6
It works great. Oh and maybe you might need to run 
sh winetricks corefonts if the fonts look alil off.

---

### Post by SunnyRabbiera on 2009-11-08
playonlinux works well too, still i like to know the make/model/isp of the original poster's modem

---

### Post by mcooke1 on 2009-11-08
What modem model is this anyhow?
Is it some generic, does it have a brand?
Certainly there must be a diagnostic you can use without IE.
Who is your provider?

Model: Ipstar iCON satelllite terminal IPX-3200  [www.ipstar.com](www.ipstar.com)
ISP:  Skymesh    [www.skymesh.net.au](www.skymesh.net.au)

---

### Post by SunnyRabbiera on 2009-11-08
Hmm my google info does not look good for that modem, it seems like it totally sucks.
A diagnostic tool that works only in one browser, friggin idiotic.
I wonder if browser spoofing works for it, did you try the diagnostic tool in firefox recently?

---

### Post by mcooke1 on 2009-11-08
> **SunnyRabbiera said:**
> Hmm my google info does not look good for that modem, it seems like it totally sucks.
A diagnostic tool that works only in one browser, friggin idiotic.
I wonder if browser spoofing works for it, did you try the diagnostic tool in firefox recently?

No, not recently but I will. Thanks

---

### Post by infinitejones on 2009-11-08
I second jcris' way of doing things... enter these one at a time into a terminal:

sudo apt-get install wine
wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
sh winetricks ie6

and it should be there under the Wine section of Applications.

However... just out of interest... what does happen when you try to access whatever it is you need to access, using a browser other than IE?

The reason I ask... there's one site I use a lot (the mapping application on [www.mapmyrun.com](www.mapmyrun.com)) that appears not to work with Firefox on Ubuntu... unless I change the "user agent" on Firefox, so that Firefox just tells the server that it's Internet Explorer, even though it isn't - and bingo, it all works.

I installed the User Agent Switcher add-on in Firefox and then the option appears in the Tools menu. It's easy, you'll work it out! 

Anyway... maybe worth seeing if that works... maybe Skymesh does something to check that IE is being used, because (misguidedly) the developers thought that was best (or couldn't be bothered to do anything else)... but at the end of the day, it might not make any difference. And it's a much simpler solution that a kludgey installation of IE6 on Wine.

---

### Post by SunnyRabbiera on 2009-11-08
> **mcooke1 said:**
> No, not recently but I will. Thanks

Its worth a try, if it doesnt work then you might need to install IE with playonlinux... which is sad.

---

