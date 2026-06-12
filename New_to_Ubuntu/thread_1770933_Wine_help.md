---
title: "Wine help"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by BigD77 on 2011-05-29
I have a laptop where I dual boot Windows XP and Ubuntu. I have Wine installed and I wanted to use Yahoo Messenger which is loaded on the Windows half.  Is that possible?  I can't download and install Messenger on the Linux side because it sees Messenger on the Windows side.

---

### Post by webofunni on 2011-05-29
You cant use the application that is already installed in Windows. You need to install it in wine. Yahoo mesn 11 seems to be in good shape 

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=22091](http://appdb.winehq.org/objectManager.php?sClass=version&iId=22091)

---

### Post by BigD77 on 2011-05-30
> **webofunni said:**
> You cant use the application that is already installed in Windows. You need to install it in wine. Yahoo mesn 11 seems to be in good shape 

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=22091](http://appdb.winehq.org/objectManager.php?sClass=version&iId=22091)

Thanks for the advice.  Now, how do you install it in Wine?  I tried to install it using Wine, but no-go, unless I did something wrong, which is more than likely the case.  Does Wine have it's own folder?

---

### Post by idoitprone on 2011-05-30
If that wine does not work, you may want to find linux native alternatives. Kopete(kde), pidgin, empathy and many others. I like pidgin simple and stupid. lol

to install somethings with wine

```
wine install.exe
```

everthing should be in you .wine directory in your home folder

[http://wiki.winehq.org/FAQ#head-497f1a295d53dd3444f211df2b13312c7767afa2](http://wiki.winehq.org/FAQ#head-497f1a295d53dd3444f211df2b13312c7767afa2)

becareful of sharing apps with windows. ^that url should explain everything

---

### Post by webofunni on 2011-05-30
Download the installer and double click on it, that should start wine. What is the error you are getting ?

---

### Post by BigD77 on 2011-05-30
I originally downloaded the file to the Desktop on the Ubuntu side.  I tried to run it, but got the message regarding .tmp files.  It was forced to close, and not install totally.

---

### Post by webofunni on 2011-05-30
Can you attach the screen shot of the error that you got ?

---

### Post by BigD77 on 2011-05-30
> **webofunni said:**
> Can you attach the screen shot of the error that you got ?

Hope this helps:[ATTACH]193679[/ATTACH]

---

### Post by webofunni on 2011-05-30
Did you install riched20 as mentioned in the how to section in the page

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=22091](http://appdb.winehq.org/objectManager.php?sClass=version&iId=22091)

?

---

### Post by BigD77 on 2011-05-30
> **webofunni said:**
> Did you install riched20 as mentioned in the how to section in the page

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=22091](http://appdb.winehq.org/objectManager.php?sClass=version&iId=22091)

?

Yes

---

### Post by BigD77 on 2011-05-30
This is what was on the terminal window when I started loading Messenger:

fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000000,(nil),0x0001,0x00000000,0x8be7ec,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:wininet:INET_QueryOption INTERNET_OPTION_CONNECTED_STATE: semi-stub
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Tue, 30-May-2013 20:00:00 GMT; path=/; domain=.yahoo.com")
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:INET_QueryOption INTERNET_OPTION_CONNECTED_STATE: semi-stub
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Tue, 30-May-2013 20:00:00 GMT; path=/; domain=.yahoo.com")
fixme:wininet:INET_QueryOption INTERNET_OPTION_CONNECTED_STATE: semi-stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Tue, 30-May-2013 20:00:00 GMT; path=/; domain=.yahoo.com")
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
err:richedit:ReadStyleSheet missing style number

---

### Post by webofunni on 2011-05-30
which version you are trying, current stable version is 10.

[http://messenger.yahoo.com/beta/win](http://messenger.yahoo.com/beta/win) 

is what looks working in wine

---

### Post by jtarin on 2011-05-30
Are there particular features of Yahoo messenger you absolutely have to have?

---

### Post by TAspr on 2011-05-30
> **webofunni said:**
> You cant use the application that is already installed in Windows. You need to install it in wine. Yahoo mesn 11 seems to be in good shape 

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=22091](http://appdb.winehq.org/objectManager.php?sClass=version&iId=22091)

Does this mean you have to have to instances of the software?

---

### Post by jtarin on 2011-05-30
Yes you must download and install the software using Wine.

---

### Post by TAspr on 2011-05-30
> **idoitprone said:**
> If that wine does not work, you may want to find linux native alternatives. Kopete(kde), pidgin, empathy and many others. I like pidgin simple and stupid. lol

to install somethings with wine

```
wine install.exe
```everthing should be in you .wine directory in your home folder

[http://wiki.winehq.org/FAQ#head-497f1a295d53dd3444f211df2b13312c7767afa2](http://wiki.winehq.org/FAQ#head-497f1a295d53dd3444f211df2b13312c7767afa2)

becareful of sharing apps with windows. ^that url should explain everything

Hello, how come I do not have the "pidgin" utility, and it is not available?  (look at pic)

---

### Post by webofunni on 2011-05-30
> **TAspr said:**
> Does this mean you have to have to instances of the software?

Wine uses its own file paths and registry entries. I dont think just executing the exe file in windows that resulted by installing the application in windows will work in wine.

---

### Post by webofunni on 2011-05-30
Yes, Pidgin is a good alternative. Even the default chat client in Ubuntu empathy works well with Yahoo. But I dont think they will support the chat rooms in messenger.

---

### Post by jtarin on 2011-05-30
> **TAspr said:**
> Hello, how come I do not have the "pidgin" utility, and it is not available?  (look at pic)Pidgin will be in the menu under the "Internet" applications. Why you don't have it I don't know. Your picture shows you have selected to show all software in the software manager. Click "installed" in the left-hand side to see installed software.

---

### Post by TAspr on 2011-05-30
> **jtarin said:**
> Pidgin will be in the menu under the "Internet" applications. Why you don't have it I don't know. Your picture shows you have selected to show all software in the software manager. Click "installed" in the left-hand side to see installed software.

Ohhh, I am sorry, this is a chat client huh?  Silly me..  I was confusing pidgin with an alternate to using WINE, sorry guys.

---

### Post by jtarin on 2011-05-30
Yea ....an alternative to Yahoo mesenger. It can connect using the Yahoo messenger protocols.

---

### Post by BigD77 on 2011-05-30
> **webofunni said:**
> which version you are trying, current stable version is 10.

[http://messenger.yahoo.com/beta/win](http://messenger.yahoo.com/beta/win) 

is what looks working in wine

Version 11.

I want the video calling from Messenger.  I have family that either doesn't use/doesn't like Skype.

---

### Post by webofunni on 2011-05-30
I am not using yahoo, just to confirm, pidgin not supporting yahoo video chat. I heard new pidgin supports video/audio.

---

### Post by BigD77 on 2011-05-30
> **webofunni said:**
> I am not using yahoo, just to confirm, pidgin not supporting yahoo video chat. I heard new pidgin supports video/audio.

Pidgin is text only.  Kopete has audio and video chat, but not for Messenger.:-({|=

---

### Post by BigD77 on 2011-05-30
Thanks for all the help.

---

### Post by jtarin on 2011-05-30
If ya gotta have video you can always stream your webcam and use it in conjunction with chat. I used to do it all the time when webcams first came out.

---

### Post by BigD77 on 2011-05-30
> **jtarin said:**
> If ya gotta have video you can always stream your webcam and use it in conjunction with chat. I used to do it all the time when webcams first came out.

Two questions.  How do you stream audio/video in conjunction with chat? 

And someone said earlier that you have to download Messenger with Wine.  Sincem that is on the Yahoo website, how is that accomplished?

---

### Post by jtarin on 2011-05-30
> **BigD77 said:**
> Two questions.  How do you stream audio/video in conjunction with chat? 

And someone said earlier that you have to download Messenger with Wine.  Sincem that is on the Yahoo website, how is that accomplished?Question One:[URL="http://www.google.com/search?q=stream+audio%2Fvideo+in+conjunction+with+cha&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a#sclient=psy&hl=en&client=firefox-a&hs=Ada&rls=org.mozilla:en-US%3Aofficial&source=hp&q=stream+webcam+&aq=f&aqi=g1&aql=&oq=&bav=on.2,or.r_gc.r_pw.&fp=3a9ced9ae85aee08&biw=1366&bih=610"]Technology was around before webcams.
[/URL]Question Two: Download messenger to your Linux desktop...then use Wine to install it in Linux.:P

---

### Post by BigD77 on 2011-05-30
> **jtarin said:**
> Question One:[URL="http://www.google.com/search?q=stream+audio%2Fvideo+in+conjunction+with+cha&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a#sclient=psy&hl=en&client=firefox-a&hs=Ada&rls=org.mozilla:en-US%3Aofficial&source=hp&q=stream+webcam+&aq=f&aqi=g1&aql=&oq=&bav=on.2,or.r_gc.r_pw.&fp=3a9ced9ae85aee08&biw=1366&bih=610"]Technology was around before webcams.
[/URL]Question Two: Download messenger to your Linux desktop...then use Wine to install it in Linux.:P

That's what I tried to do....I downloaded it to my desktop and tried to install it with Wine.

---

### Post by jtarin on 2011-05-30
Post your terminal commands and results for installing.Use the #code# tags when responding with terminal info.

---

### Post by BigD77 on 2011-05-30
> **jtarin said:**
> Post your terminal commands and results for installing.Use the #code# tags when responding with terminal info.

dennis@dennis-laptop:~/Desktop$ wine msgr10us.exe
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),1,3,(nil),0,(nil)) - stub!
fixme:advapi:RegisterEventSourceW ((null),L"YahooAUService"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000000,(nil),0x0001,0x00000000,0x8be7ec,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:wininet:INET_QueryOption INTERNET_OPTION_CONNECTED_STATE: semi-stub
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Tue, 30-May-2013 20:00:00 GMT; path=/; domain=.yahoo.com")
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:INET_QueryOption INTERNET_OPTION_CONNECTED_STATE: semi-stub
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Tue, 31-May-2013 20:00:00 GMT; path=/; domain=.yahoo.com")
fixme:wininet:INET_QueryOption INTERNET_OPTION_CONNECTED_STATE: semi-stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Tue, 30-May-2013 20:00:00 GMT; path=/; domain=.yahoo.com")
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!

---

### Post by idoitprone on 2011-05-31
i just tried installing msn messager 10 whatever and it crashes.

trying to access something from the internet

btw, this is only the native alternative i can think of for yahoo chat

[http://ubuntuforums.org/showthread.php?t=773802](http://ubuntuforums.org/showthread.php?t=773802)

gyachi

---

### Post by BigD77 on 2011-05-31
> **idoitprone said:**
> i just tried installing msn messager 10 whatever and it crashes.

trying to access something from the internet

btw, this is only the native alternative i can think of for yahoo chat

[http://ubuntuforums.org/showthread.php?t=773802](http://ubuntuforums.org/showthread.php?t=773802)

gyachi

Does that have audio/video, or is it just text?

---

### Post by idoitprone on 2011-05-31
[http://en.wikipedia.org/wiki/Gyachi](http://en.wikipedia.org/wiki/Gyachi)

i believe it is the closest open source alternative the propriotery yahoo client.

I believe it can do chat, dont take my word do a little research on it since i do not use it

btw pidgin is only text and empathy does have chat, but it might not supppport the yahoo chat protocol. I never use so i do not know

---

