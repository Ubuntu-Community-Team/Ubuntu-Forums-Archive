---
title: "Dial-Up Woes"
date: 2005-07-24
forum: Networking &amp; Wireless
---

### Post by Tylo on 2005-07-24
Hello. I have a 127a: 1005  Serial controller: Rockwell International HCF 56k Data/Fax/Voice/Spkp (w/Handset) Modem. I identified this with the help of the tool scanModem.

Now, somehow I overlooked the fact that it said it was an HCF modem. This particular type of modem can be either HSF or HCF, thus requiring the corresponding driver.

I got the drivers from [http://www.linuxant.com/drivers/](http://www.linuxant.com/drivers/) as just about everyone does that has this particular type of modem.

Of course, I installed HSF first, with no success. Afterwards, I installed the HCF drivers. I noticed during installation that these two lines appeared.

[INDENT]Note: kernel module snd-intel8x0m overridden by hsfmc97ich hsfmc97sis
Note: kernel module snd-atiixp-modem overridden by hsfmc97ati[/INDENT]

My theory is that the HSF modem drivers are somehow interfering with my installation of the HCF drivers.

My first question is, then, how do I uninstall these HSF drivers?

Interestingly, even with this possible problem, I *believe* the modem still connects to the internet. I say *believe* because no internet applications are able to connect to anything, but when I pick up my receiver the standard internet noise is there. Also, my log showed that I was connected for 51 minutes at one point. However, it only seems to work until I restart Ubuntu. After the restart, it no longer works, so I have to reinstall the HCF drivers.

My second question is, what the heck is up with that?  :smile:

---

### Post by Tylo on 2005-07-24
Well, I am glad to say that I am making this post with the Ubuntu OS running.  \:D/ 

I figured out how to uninstall the HSF drivers using Synaptic. It was pretty easy, actually. I Just found the hsfmodem listing, marked it for uninstalling, and updated the listings. If anyone else has this trouble, I hope you run across this message.

However, one thing of note is that I couldn't get web applications(Firefox, GAIM, etc.) to recognize the dial-up connection until I deactivated my ethernet card under System->Administration->Networking.

I believe this may have something to do with being integrated with a network set up with Windows XP that has Internet Connection Sharing set-up. I'll see if I can get the Internet Connection Sharing disabled on the XP machine and report back the results. For reference, I am using a DI-604 router.

It's unknown if the HSF drivers I installed previous to the HCF drivers were causing the dial-up to not function. My guess is that they were not, since the dial-up was acting the same before and after uninstalling the HSF drivers.

As for the modem not functioning after restarting Ubuntu, it no longer does this. So the HSF drivers may have been causing that, or perhaps I am just senile.

---

