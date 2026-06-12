---
title: "how to run Firefox in wine?"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by paker on 2009-02-22
I need to run FireFox in wine.
In terminal what do I type after wine?
Or should I install a separate FireFox in wine?
Thanks.

FireFox 3.06
Ubuntu 32 bit 8.10

Background: I installed a FireFox plugin (Scorch) for Windows. Scorch is a music score program. I think I need to run FireFox in wine to activate the plugin.

---

### Post by SunnyRabbiera on 2009-02-22
You sould not need any commandline to install firefox under wine, once wine is installed you should be able to just install the windows firefox like you do in windows.
But you may want to play around with wineconfig first.

---

### Post by pdtpatrick on 2009-02-22
LOL why would u want to run firefox in wine when it works better on the platform itself? Very odd.

---

### Post by staf0048 on 2009-02-22
I think you'll need to install the windows version of FF inside wine to get it to work.  What a pain!!  I'm surprised it's not available for Linux . . .

---

### Post by llamabr on 2009-02-22
It might be difficult to do, and I have no idea why you would want to do that.

Why do you want to do that.  I suspect that whatever you want to do, there's a better way to do so.

Wine is almost always the wrong idea.

---

### Post by T2manner on 2009-02-22
I guess you would just download the firefox exe for windows and install it normally.

---

### Post by SunnyRabbiera on 2009-02-22
In any case it should be simplistic and easy...
No rocket science needed :D

---

### Post by llamabr on 2009-02-22
I guess you could try.  But since that will probably fail, why would you want to do this?

---

### Post by paker on 2009-02-22
> **SunnyRabbiera said:**
> You sould not need any commandline to install firefox under wine, once wine is installed you should be able to just install the windows firefox like you do in windows.
But you may want to play around with wineconfig first.

> **pdtpatrick said:**
> LOL why would u want to run firefox in wine when it works better on the platform itself? Very odd.

Should I download a Windows version FireFox and install it under wine?
Boy, it's getting complicated. Please confirm. Thanks.

There is a website called cyberhymnal.com. They have downloadable scores in Sibelius (Scorch) format. And Sibelius runs in Windows only. I know it sounds strange.

---

### Post by SunnyRabbiera on 2009-02-22
> **llamabr said:**
> I guess you could try.  But since that will probably fail, why would you want to do this?

Firefox 3.0.6 works fine under wine

---

### Post by llamabr on 2009-02-22
> **SunnyRabbiera said:**
> Firefox 3.0.6 works fine under wine

Could be, but my suspicion is that whatever the OP is trying to do, it could be done much more parsimoniously without running wine.

Wine is almost never the right answer.

---

### Post by matteojg on 2009-02-22
In order to run a program in wine you  need to install that program in the fake windows directory.

My advice, however, would be to find a comparable plug-in that works in the native environment.

---

### Post by SunnyRabbiera on 2009-02-22
> **paker said:**
> Should I download a Windows version FireFox and install it under wine?
Boy, it's getting complicated. Please confirm. Thanks.

There is a website called cyberhymnal.com. They have downloadable scores in Sibelius (Scorch) format. And Sibelius runs in Windows only. I know it sounds strange.

Go ahead, it will work I assure you.
Firefox 3.0.6 is very wine friendly

---

### Post by paker on 2009-02-23
> **matteojg said:**
> In order to run a program in wine you  need to install that program in the fake windows directory.

My advice, however, would be to find a comparable plug-in that works in the native environment.Thanks for the confirmation. I will go ahead and install a separate FireFox. I hope it doesn't mess up the native FireFox.

Regarding your second point, I have already searched this forum. No one has found a solution yet. I MUST have a Scorch plugin in the browser to open the sheet music, and the plugin runs ONLY in Windows. It is one of the last few Windows thingy I want to graduate from but haven't yet.

---

### Post by SunnyRabbiera on 2009-02-23
A install of firefox in wine will do no harm to your linux version.
Both use separate directories

---

### Post by stoogiebuncho on 2009-02-23
There was an article recently that showed that (for at least the person running the tests) the Windows version of Firefox ran faster through wine than the linux version did natively.

So maybe there's a reason after all. ;)

[http://www.tuxradar.com/content/browser-benchmarks-2-even-wine-beats-linux-firefox]("http://www.tuxradar.com/content/browser-benchmarks-2-even-wine-beats-linux-firefox")

---

### Post by novafluxx on 2009-02-23
> **stoogiebuncho said:**
> There was an article recently that showed that (for at least the person running the tests) the Windows version of Firefox ran faster through wine than the linux version did natively.

So maybe there's a reason after all. ;)

[http://www.tuxradar.com/content/browser-benchmarks-2-even-wine-beats-linux-firefox]("http://www.tuxradar.com/content/browser-benchmarks-2-even-wine-beats-linux-firefox")

wow!

---

### Post by paker on 2009-02-23
Thanks. FireFox is running under wine, but the plugin is not working right. I will post a separate question in the Wine Forum. Thanks again.

---

### Post by Kellemora on 2009-02-24
I tried loading the winDOZE version of Firefox in Wine because some web sites I need to visit use Shockwave and will not work in the Linux Version of Firefox with the ShockwaveEmulator plug-in, needs the Windows version only.  However, Shockwave don't work in Wine as a plug-in to Firefox, so I just uninstalled the whole mess.

I did not see that Firefox in wine was faster than the Linux version, in fact, it was quite the opposite.

I get web links in my Eudora e-mails running in wine and they open the Linux version of Firefox instantly.

The only problem is, attachments to files I have to manually go into drive_C and locate them, and open them with an applicable program in Ubuntu while outside of Wine.

If Firefox opens, why not other programs like Evince for pdf attachments, or mplayer for audio, etc.?

TTUL
Gary

---

