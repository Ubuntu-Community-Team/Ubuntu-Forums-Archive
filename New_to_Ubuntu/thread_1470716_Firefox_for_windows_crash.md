---
title: "Firefox for windows crash"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by uban2 on 2010-05-03
hi all users,

i want to use Shockwaveplayer on Ubuntu/Linux.

so as below, I installed Firefox 3.6.3 for windows on my PC using wine. 
but when i try to open Firefox for windows, i always received the message,
"crash, sorry for incenvenience" 
it doesn't work. 

i have no problem opening "Firefox for Linux", 
it's working very well. 
i don't know why. 

[IMG]file:///C:/DOCUME%7E1/%E3%81%82%E3%81%A4%E3%81%8D/LOCALS%7E1/Temp/moz-screenshot.png[/IMG] 
please help me. 


[B]
(from [/B][Ubuntu Documentation]("https://help.ubuntu.com/")**)**[FONT= ]**Installation**[/FONT][FONT= ]****[/FONT]
[FONT= ]Unfortunately, the Shockwave player is only available for Windows. On a PC, 
[/FONT]
[FONT= ]it may be possible to run Shockwave under Ubuntu using [/FONT][[COLOR=#0000FF][FONT= ]_Wine_[/FONT][/COLOR]]("https://help.ubuntu.com/community/Wine")[FONT= ] 
[/FONT]
[FONT= ]and running the Windows versions of Firefox and the Shockwave player. 
[/FONT]
[FONT= ](Wine does not work on PowerPC and may not work as expected on 64-bit PCs.) 
[/FONT]
[FONT= ]You can then use [/FONT][FONT= ]**mozplugger**[/FONT][FONT= ], a program that lets you "embed" other programs in your web browser. [/FONT][FONT= ][/FONT]
[FONT= ]First, install the wine and mozplugger packages (for information on how to do this, see [/FONT][[COLOR=#0000FF][FONT= ]_InstallingSoftware_[/FONT][/COLOR]]("https://help.ubuntu.com/community/InstallingSoftware")[FONT= ]). [/FONT][FONT= ][/FONT]
[FONT= ]sudo apt-get install wine mozplugger[/FONT][FONT= ][/FONT]
You then need to install the **Windows** version of Firefox  (yes, you read that right). Download it from [Mozilla's web site]("http://www.mozilla.com/firefox/all.html").   Choose to open the installer with Wine and follow the on-screen  instructions.

---

### Post by GSF1200S on 2010-05-03
> **uban2 said:**
> hi all users,

i want to use Shockwaveplayer on Ubuntu/Linux.

so as below, I installed Firefox 3.6.3 for windows on my PC using wine. 
but when i try to open Firefox for windows, i always received the message,
"crash, sorry for incenvenience" 
it doesn't work. 

i have no problem opening "Firefox for Linux", 
it's working very well. 
i don't know why. 

[IMG]file:///C:/DOCUME%7E1/%E3%81%82%E3%81%A4%E3%81%8D/LOCALS%7E1/Temp/moz-screenshot.png[/IMG] 
please help me. 


[B]
(from [/B][Ubuntu Documentation]("https://help.ubuntu.com/")**)**[FONT= ]**Installation**[/FONT][FONT= ]****[/FONT]
[FONT= ]Unfortunately, the Shockwave player is only available for Windows. On a PC, 
[/FONT]
[FONT= ]it may be possible to run Shockwave under Ubuntu using [/FONT][[COLOR=#0000FF][FONT= ]_Wine_[/FONT][/COLOR]]("https://help.ubuntu.com/community/Wine")[FONT= ] 
[/FONT]
[FONT= ]and running the Windows versions of Firefox and the Shockwave player. 
[/FONT]
[FONT= ](Wine does not work on PowerPC and may not work as expected on 64-bit PCs.) 
[/FONT]
[FONT= ]You can then use [/FONT][FONT= ]**mozplugger**[/FONT][FONT= ], a program that lets you "embed" other programs in your web browser. [/FONT][FONT= ][/FONT]
[FONT= ]First, install the wine and mozplugger packages (for information on how to do this, see [/FONT][[COLOR=#0000FF][FONT= ]_InstallingSoftware_[/FONT][/COLOR]]("https://help.ubuntu.com/community/InstallingSoftware")[FONT= ]). [/FONT][FONT= ][/FONT]
[FONT= ]sudo apt-get install wine mozplugger[/FONT][FONT= ][/FONT]
You then need to install the **Windows** version of Firefox  (yes, you read that right). Download it from [Mozilla's web site]("http://www.mozilla.com/firefox/all.html").   Choose to open the installer with Wine and follow the on-screen  instructions.

Where do you get that error message (is it a popup)? You could try running firefox through wine via the terminal. For example:
```
wine /path/to/firefox.exe
```
Be careful if it has spaces (like Program Files)- you will need to enclose the command in " " marks. For example, heres how I start Diablo 2:
```
wine "/home/poeticrpm/.wine/drive_c/Program Files/Diablo II/Game.exe"
```

When it crashes, see what wine spits out in the terminal and paste it here. Perhaps youre missing a .dll or something..

---

### Post by JPorter on 2010-05-11
> **uban2 said:**
> hi all users,

i want to use Shockwaveplayer on Ubuntu/Linux.


The term "Shockwave" is sometimes confusing, because it used to refer to a whole range of Flash-based content on the web.  That's no longer true.  If it's the Flash plugin that you need for web-embedded Flash content, it is available directly in the Ubuntu repositories and works just fine in Firefox.  The browsing experience should be very similar to what you experience in Windows.

The plugin can be installed from the Ubuntu Multiverse repository, where it is called [FONT="Courier New"]flashplugin-installer[/FONT], or from the Ubuntu Partner repository, where it is called [FONT="Courier New"]adobe-flashplugin[/FONT].


The reason I've posted this is because I've seen a number of people who combine Flash and Shockwave into one concept and assume based on very old (2005, 2006) information that Ubuntu does not have Flash support.  If you actually need the full Adobe Shockwave player specifically for Adobe Director content, that's a different issue.

Please post if this solves your issue, or if you have more questions.


Best of luck,

Jason Porter

---

