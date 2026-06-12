---
title: "Trying to add a wine application I've added in other Ubuntu systems, but not working"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by swarup on 2009-05-16
I am running Jaunty in a Dell M6400 laptop. I have a collection of electronic books with an index and search program to run searches on them. This is a Windows-based text-index and search utility, and I have installed it successfully using WINE in many earlier versions of Ubuntu as well as in another computer running Jaunty. But in my DELL M6400 when I installed it, initially it wouldn't install because it was trying to install it back onto the CD itself which of course it had no permission to do (the CD was not rewritable). So I reset the target location for the install, to my home directory. It then installed fine. And the program opens fine as well, and appears completely normal. But I cannot type anything in the search window, nor can I run any searches. The program just sits there looking beautiful, but won't do anything. I've never come across this before.

How can I trouble-shoot this, so as to get the program working?

---

### Post by Sir Jasper on 2009-05-16
Hi,

You might try making sure the cursor is within the Wine widow and perhaps trying it in different positions.

My regards

---

### Post by swarup on 2009-05-16
I'm not certain just what you mean, but the program as installed is definitely not working. I am extremely familiar with the program, and use it all the time in other computers, via Wine. But in this computer it has not installed properly. I guess I'd like to uninstall it and try reinstalling it. Can someone tell me how to uninstall an application which I've installed through wine?

---

### Post by Electron on 2009-05-16
To unistall:
Application>Wine>Unistall software; then you probably has to delete by hand any desktop icons created during installation.

Also, I have a similar problem with one of mine windows application and the problem was that the application needed microsoft fonts  to work. I don't think that's your problem but check it out. Best wishes.

---

### Post by sandyd on 2009-05-16
Also, I have a similar problem with one of mine windows application and the problem was that the application needed microsoft fonts  to work. I don't think that's your problem but check it out. Best wishes.[/quote]
if the poster's suggestion is correct........, then......
```

sudo wget [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)
sudo mv winetricks /usr/bin
sudo chmod 777 /usr/bin/winetricks
winetricks allfonts fontfix

```Winetricks is a pretty useful app for installing windows programs such as directx, windows media player, and all sorts of crazy stuff.

---

### Post by swarup on 2009-05-16
@carlee: Thanks for the tip. I don't know that the fonts are the problem, as I have installed this app using Wine in several computers in the past and the fonts were never an issue-- but I'll try your suggestion and see what happens. :p

---

### Post by swarup on 2009-05-16
Well, Thanks to both of you!!!!!!!!!!!!
I installed Winetricks as Carlee suggested, and the program is working now. This is the oddest thing. I just don't know why this would be like this, when I never had to do this in any other computer in which I installed this app. But anyway, thank you. :p

---

### Post by swarup on 2009-05-16
Well, I don't know if that was the solution or not. I closed the program and reopened it, and again it is not working. I have to add that initially, after installing Winetricks and then opening my app, it did not work. But there is an option in the app for "check for online update". It is of course an update for the Windows application, but out of desperation, I tried clicking on it. It actually did a download (showing a download progress bar and everything), and then at the end of the download announced, very strangely, that it "could not connect to the website". And it did not seem that any download/update was ultimately installed. But despite the apparently failed update attempt, the program started to work! I assumed it to be not due to the failed update attempt, but rather to carlee's Winetricks. So I closed the app and reopened it to see if it would work. It again would not allow me to type in the search window! I again tried the online update. Again it did the download, and then announced it could not connect to the website. And again, after the failed update the app started working properly. So perhaps every time I want to use this app on this machine, I'll have to open the app and run a failed online update, after which it will work!?!?! How odd. Anyhow, at least I can get it to work. :p

If anyone has any further suggestion on how to get the app to run without having to run a failed "online update" every time, I'm all ears.

UPDATE: I have realized that I do not need to run the online update every time. All I need to do is open the app, go to help->"about" and let the app announce its version in a little window. Once I do that, then the app starts working. Just a little quirk, I guess. But it only takes a moment to do, and is painless.

---

