---
title: "Using RSA Soft Token"
date: 2008-07-09
forum: Networking &amp; Wireless
---

### Post by shahzeb.ihsan on 2008-07-09
Hi,

I use a soft remote access token to log in into my work network from home using Windows XP. Sometimes I have to work from within Linux also, but I can't remote login to my work network because the the RSA SecurID software is only available for Windows. My question is, is there a replacement for SecurID for Windows or is it possible to use WINE to run SecurID?

Thanks,
Shahzeb

---

### Post by HalPomeranz on 2008-07-10
There is no Linux replacement that I know of.  I'm not sure about Wine, but you could certainly run the software inside of VMware or Virtualbox.

---

### Post by OldAndTired on 2010-01-09
> **HalPomeranz said:**
> There is no Linux replacement that I know of.  I'm not sure about Wine, but you could certainly run the software inside of VMware or Virtualbox.
Don't want to run an entire virtual OS just to have this widget, needed for 5 seconds, working.

Tried wine.  After installing req'd libraries got as far as storing key.  RSA couldn't find any devices.  Should be able to find "drive c".  Don't know if this needs to be addressed via RSA soft-token or wine.

Getting VPN to work going is the last thing I need to free me from Vista.  I hope someone out there can help me break my chains.

---

### Post by edge30 on 2010-01-31
Hi
Same situation here, anyone out there to help?
I'm also in the situation were having VPN working is the only key missing in he puzzle to be free from Windows 7.
Please...

---

### Post by sarv666 on 2010-04-01
Just trying to revive interest here because it would seem that the issue is still open and you can add me to the list of interested parties for this topic.

What I've done so far:
1.) Installed vpnclient (steps can be found here [http://www.painfullscratch.nl/code/vpn/](http://www.painfullscratch.nl/code/vpn/))
2.) copied the vpn profile
3.) tried to connect using the vpn profile, e.g. vpnclient connect europe (where europe.pcf exists in the global profile directory)

I also had a very quick look at vpnc
A.) had to get a copy of pcf2vpnc (and associated stuff)
B.) ran it on my europe.pcf profile
C.) used the values to try and login using it.

No luck on either approach. Have to say though that I feel I was closer to a solution with vpnclient but unfortunately don't know enough CISCO vpn to say. However, I know that I don't have a RSA soft token in linux, so I think that's where my problem lies. 

Thx.

---

### Post by pm_4u on 2010-05-13
Hello guys ,
Any Luck ? 
Even I am looking for a solution.
 
Thanks !

---

### Post by MrSqueezles on 2010-05-14
I used the Soft Token app under Karmic without problems.  I just got a new computer and put Lucid on it and can't get the app to start.  It installs, but says "Error loading desktop client".  I did get a message about a missing library, but upgrading to the latest Wine beta got rid of it.  Now, it quits without any console errors.

:confused:

---

### Post by pm_4u on 2010-05-14
Hello , 

Can you please tel me.. what you did to make RSA softoken run under Karmic koala ?

Your reply will be a big help !

Thanks !

---

### Post by pm_4u on 2010-05-17
I could make RSA soft token work.

I used the WINE to install RSA on Karmic koala(9.10) using the following soft token version.(RSA SecurID Software Token for Windows Desktops)

[http://www.rsa.com/node.aspx?id=1162]("http://www.rsa.com/node.aspx?id=1162")

Thanks !

---

### Post by MrSqueezles on 2010-05-27
I didn't really do anything.  The 4.1 version just worked.  I wish I could give you some advice :)

---

### Post by Styles on 2010-09-01
Hi all,

     I ran into this thread looking for more information about libradiusclient. Anyway I'm authenticating against our RSA server and a Hard token, using libradiusclient via PPTP and PAM. Maybe this will help point you guys in the right direction, but I had some issues, see my previous thread here 

[http://ubuntuforums.org/showthread.php?t=1517219](http://ubuntuforums.org/showthread.php?t=1517219)

Cheers,
Eric

---

### Post by MrSqueezles on 2010-10-04
A while ago, I got a new laptop and haven't been able to run the SecurID software.  After talking with some coworkers, we think that it's because we're using 64 bit Ubuntu.  I'm going to look into whether Wine can run apps in 32 bit mode.

---

### Post by carlo bolzonello on 2011-01-06
Hi Guys,

I have been looking for a long time for a RSA Software token for linux, the closet i have come is this, i haven't done more than find the link, but am going to put a lot of effort in to getting this to work now, need to move :p

have a look here
[http://www.rsa.com/node.aspx?id=2521](http://www.rsa.com/node.aspx?id=2521)

Lets see if we can get this to work and solve our issue.

---

### Post by carlo bolzonello on 2011-01-06
I have the converter, you need to run this on windows and follow instructions inside the zip, please feedback to all with progress.

---

### Post by mOOky on 2011-04-05
This works brilliantly on Ubuntu 10.10.  I downloaded the Wine beta package from the Ubuntu Software Manager, installed the font package, and then did the 'wine msiexec -i ./RSASecurID410.msi' and it found my keyfile automatically.  Works perfectly (compared to the softoken on my BB and they are identical).

Yay WINE!

---

### Post by jpborjas on 2011-11-07
Mooky, where did you run this from? Mine installs, but after telling it where the profile file is (.sdtid), it didn't find the drive to save the token to. I'm running wine 1.3.31

Thanks

---

### Post by jpborjas on 2011-11-07
Ah, figured it out. I just navigated to the folder where the msi file was, but inside the wine/windows structure: 

~user/.wine/dosdevices/c:/users/user/

I just double-clicked it and it installed just fine. Sorry if this is obvious to seasoned Wine user, as I'm not. This is my first Wine adventure, and I'm loving it!

---

### Post by vmunix on 2012-04-15
Hello All,
Just to update, the RSA secure id version "RSASecurIDToken411" works very well with Wine version 1.4 in Ubuntu 12.04 LTS. All I had to do was download this 4.1 version and install it through wine. After that just imported the stdit file from the wine c:\ drive. Everything went fine.

The RSA Secure ID file version 4.0 was not working with Ubuntu 12.04 LTS. It was not able to see the drive after all my efforts.

---

