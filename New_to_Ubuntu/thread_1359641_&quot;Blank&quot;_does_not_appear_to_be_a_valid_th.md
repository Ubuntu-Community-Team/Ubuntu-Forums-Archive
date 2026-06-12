---
title: "&quot;Blank&quot; does not appear to be a valid theme - Error"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by Dallasguy on 2009-12-19
I am a Ubuntu noob and just downloaded it today.  I have been playing with it and decided to DL some themes.  However, both themes are giving me the "___ does not appear to be a valid theme" error and not sure why.

I DL'ed two themes and not sure where to save them....there was not an option to save them in themes folder.  I went to home folder and used ctrl + H to open up hidden folders.  I found them and tried opening them using the Theme Installer and Appearance.

I see them under downloads as well but not sure what to do with them from here.  

Any suggestions?   FYI, the ones that I DL'd are Xarion-Compiz and Human Pabloblack Emerald.

---

### Post by orlox on 2009-12-19
I couldnt find your xarion compiz theme. With respect to the other one, that's an emerald theme. To use it, you first need to install emerald. Before trying that, I'd recommend you to try out some regular themes first so you don't need to do any additional stuff.

You can look for popular themes [here]("http://gnome-look.org/index.php?xcontentmode=100"). Most of the times, to install them, you need to open system->preferences->appearance, and drop the file you download in there.

---

### Post by Dallasguy on 2009-12-19
Clarification, I used wubi that runs on Windows so not a true install.

---

### Post by Dallasguy on 2009-12-19
Orlox, thanks for your reply.  

Here is a link to the Xarion, [http://compiz-themes.org/content/show.php/Xairon-Compiz?content=70828](http://compiz-themes.org/content/show.php/Xairon-Compiz?content=70828) .

I will check out your link before having to do any extra dl as you suggested.

Thanks for the help.

---

### Post by orlox on 2009-12-19
From that link, I can see that Xarion is also an emerald theme, not a standard theme. If you want to try out emerald, go to:

system->administration->synaptic package manager

and look for the package "emerald" and install it.
To try it out, you can press alt+f2 and run
```
emerald --replace
```
I believe that under system->preferences you should have a new entry referring to the configuration of emerald, and you can use that to install the other themes you mentioned.

---

### Post by Dallasguy on 2009-12-19
Now I have the Emerald Theme Manager and select the theme.  When I double click the theme it does nothing.  How do I make the selected theme the actual theme?

---

### Post by Dallasguy on 2009-12-20
Ok, I clicked on the emerald theme that I want, typed "emerald --replace" in terminal, and added it tothe startup application.  However, the changes never applied.  I even rebooted and nothing.

Any suggestions?

---

### Post by orlox on 2009-12-20
So, your theme applied correctly, and emerald worked running emerald --replace, and you can't get it working on startup??

---

### Post by orlox on 2009-12-20
Just checked back on how to run emerald at startup.

Remove what you added on startup apps, and using synaptic, install the package compizconfig-settings-manager. Then, under system->preferences you should now have an entry to configure compiz. Enter there, look for "window decorations", and in the "command" option select put "emerald --replace". On reboot, emerald should be working for you.

You can also play with the compiz configuration to see all the nice effects available

---

### Post by orlox on 2009-12-20
Also, I should mention that the theme won't apply by simply double clicking it. You must install it using the emerald theme manager under system->preferences

---

### Post by Dallasguy on 2009-12-20
"So, your theme applied correctly, and emerald worked running emerald --replace, and you can't get it working on startup??"

The emerald theme is not working at all. 

This is what I tried: System>Preference>Emerald Theme Manager>select a theme>I open up terminal and type "emerald --replace" without quotes>close both the Emereld Them Manager and terminal.  There is no change.

I read somewhere that I have to apply this change at startup as well so I ....System>Preference>Startup Applications>click on Add>Type the command and name>click on Add>close.

---

### Post by orlox on 2009-12-20
I'm still not clear if you managed to run emerald. Do your window borders change after running the emerald --replace command?

Also, after applying a theme, it's not neccesary to reboot. You just need to add it in the emerald theme manager using "import...", and then simply select it.

If after using the "emerald --replace" command your window borders don't change, then something is going wrong...

---

### Post by Dallasguy on 2009-12-20
Yes, that is correct.  The borders are not changing at all.  It looks exactly the same as before running emerald --replace command.

Maybe I should try from scratch and dl emerald.

---

### Post by orlox on 2009-12-20
> **Dallasguy said:**
> Yes, that is correct.  The borders are not changing at all.  It looks exactly the same as before running emerald --replace command.

Maybe I should try from scratch and dl emerald.

I don't think that's neccesary. It's probable that you haven't activated the desktop effects yet. Go to system->preferences->appearance and under the "visual effects" tab, choose normal or extra. After that, you should be able to activate emerald, and you will also have a lot of nice effects...

---

### Post by Dallasguy on 2009-12-20
Oh, wow! Nice effects!  I notice when I close the terminal then the effects are gone.  Do I keep the terminal open or is there a proper way to close?  I do notice that is says "There is still a process running on this terminal. Closing the terminal will kill it".  I assume it is referring to the effects.  

What is the proper way to close the terminal window and keeping the effects?

---

### Post by chaanakya_chiraag on 2009-12-20
The easiest way is to press <Alt>F2 and enter in the command ```
emerald --replace
```  That should work :)

---

### Post by Dallasguy on 2009-12-20
Chaanakya,

After I type in that command the terminal window stays open.  When I close the window then the effects go away.  My question is how do I close the window without losing the emerald effects?

---

### Post by Dallasguy on 2009-12-20
Chaanakya, I stand corrected.  You are correct.  Alt F2 will bring up a different window and closing after I type command and hit Run.

THanks!

---

### Post by orlox on 2009-12-20
dallasguy, if you now follow the instructions of post #9 (in the first page of this thread) you will have emerald working at startup, and you will also have a program to configure your desktop effects.

Adding emerald --replace at startup applications should work, but it's not the optimal way to do it.

---

### Post by Dallasguy on 2009-12-20
Orlox, I am making those startup changes now.

With your help I finally have emerald on, however, the themes are not working after selecting them.  I select theme>alt +F2>type emerald --replace>and nothing happens.

I am starting to become frustrated.

---

### Post by orlox on 2009-12-20
How are you installing your themes?? Are you using the emerald theme manager? If so, can you see a preview of the theme in there?

A small preview should be shown there, and just by clicking it your windows should refresh to that theme.

Also, be aware that the theme must be a file with a .emerald termination. Sometimes, themes are distributed in compressed files, probably something like tar.gz, and those need to be extracted so you can get the .emerald file.

---

### Post by Dallasguy on 2009-12-20
Wow, while you were responding I realized that I had to extract one of the themes that I dl'd.  After doing so I was able to select it from emerald theme manager, see the preview, and then did the emerald --replace.  I did notice that the borders of windows changed color but everything else is the same.

---

### Post by orlox on 2009-12-20
Alright, an image is worth a thousand words...

So, for the xarion theme you downloaded. It comes in a compressed format, .tar.gz, which is something like zip (but better).

So, each of the images attached are:

[LIST=1]
[*]Double clicked on the theme file, it shows me the files included in the tar.gz
[*]Navigated inside the folder, I can see a lot of .emerald files. Each of these is a theme, and they're slightly different
[*]Extracted all the themes to a folder
[*]Using the emerald theme manager, I installed one of the themes using the import button
[*]Selected the theme, which applies it
[/LIST]

And thats it :D

---

### Post by orlox on 2009-12-20
> **Dallasguy said:**
> Wow, while you were responding I realized that I had to extract one of the themes that I dl'd.  After doing so I was able to select it from emerald theme manager, see the preview, and then did the emerald --replace.  I did notice that the borders of windows changed color but everything else is the same.

Emerald is what is called a window-decorator. It doesn't modify the look of the apps, but only of the window borders.

If you want to modify the rest, you should check [here]("http://gnome-look.org/index.php?xsortmode=high&page=0&xcontentmode=100") (this is the same link I provided you a while ago). Note that as long as you have emerald activated, these themes wont alter your window decorations.

---

### Post by Dallasguy on 2009-12-20
Orlox, I owe you some beers for putting up with me.  I didn't realize that it was for borders only.  I thought it would change the entire thing.  When I looked at the themes, I saw different icons for everything.  One theme that I looked at was similar to Mac where it had the icons lined up in bottom center screen.  I thought this was included in the theme.

When you told me about Emerald.....well, I had no idea what that was...since I was a noob I thought that is just a special kind of theme.

Again, thanks for your help.  I am going to bury my head in sand now.

---

### Post by orlox on 2009-12-20
The icons on the bottom are easy to get. That is called a dock, and there are several available. I personally like docky, which is a relatively young one, that's rapidly improving.

If you installed ubuntu 9.10, then you could follow [these instructions]("http://www.youtube.com/watch?v=WmE4dC-P3GQ") to get it installed.

Icons are also installed aside. In the site I gave you, gnome-look.org there's a whole section dedicated to icons.

---

### Post by orlox on 2009-12-20
And don't worry about beeing a noob. Everyone is one at the beggining.

---

