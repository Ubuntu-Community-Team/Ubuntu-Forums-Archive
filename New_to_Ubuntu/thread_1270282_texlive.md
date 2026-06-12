---
title: "texlive"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by hellzalkemist on 2009-09-19
Hello. I installed the texlive-full package through Synaptic Package Manager and the installation was succesful. However I cannot find any new applications added for me to use it. I heard latex is great for writing Mathematical stuffs.
Thanks.

---

### Post by XCan on 2009-09-19
Latex is not really a graphical application, thus you won't find it in the menu. What you do is to write a document in latex-code (very easy compared to programming code), and compile it, i.e., write a document in draft.tex and compile it with ```
 latex draft.tex 
```

Although latex in very many ways is better than WYSIWYG editors, getting into it will take you a few moments. There are many tutorials around, I can't recommend any as I got into the whole thing by simply being given a latex document for an article. However, I do recommend [http://en.wikibooks.org/wiki/Latex](http://en.wikibooks.org/wiki/Latex) for reference.

Oh, there are also editors available that will help you. I use gedit+latex plugin, but there are more advanced (in my opinion bloated) editors in the repos.

---

### Post by Temposs on 2009-09-19
If you want more of a GUI, there are options.

the program called LyX is probably the easiest way to get started with LaTeX.

Another alternative, the solution I actually use, is the gedit-latex-plugin. You can install that from synaptic. It's for the Ubuntu "text editor" which is called gedit. When you open a .tex file in gedit with this plugin installed, it shows a lot of useful latex tools that makes writing latex a lot easier.

---

### Post by entropy1 on 2009-09-19
I have used gedit with the latex pluggin, and that works quite well.  However, I prefer texmaker.  But you need the latest version, which is not in the repositories.  To read about texmaker, go to

[http://www.xm1math.net/texmaker/](http://www.xm1math.net/texmaker/)

Click on the "download" link to see choices, e.g.,

Static i386 binary DEB package : texmaker_1.9.2-1_i386.deb (for DEBIAN-based Linux distributions : Ubuntu, debian, etc...)

or

Static amd64 binary DEB package : texmaker_1.9.2-1_amd64.deb (for DEBIAN-based Linux distributions : Ubuntu, debian, etc...)

After downloading, right click the file and choose   Open with "GDebi Package Installer"

---

### Post by hellzalkemist on 2009-09-20
thanks a lot. that was really helpful.

---

### Post by wannabegeek on 2009-10-01
Good day,

I am a complete noob, with just a little Unix experience here and there....

I would like to get the gedit plugin to work and haven't had much luck. I found some forum articles dealing with how to get it , but it must have been for a different installation.

I am running Hardy. 

Also, I tried to get a GUI called Gummi, which looked really cool and lite weight, however
I don't have all the Python files it wants and it's been a mess trying to sort that out.

I did have some success when I tried Latex in terminal. The output went to the desktop,
however, the math symbols did not work.

I used to use the amsmath and amsfont packages in my windoze days, when I ran TeXnic Center, it manages all the packages and auto downloads if a nwe one shows up in the preamble.

If anyone can offer some advice that would be great I need to write some reports soon.

TIA,
wannabegeek

---

### Post by XCan on 2009-10-01
Did you get the plugin from [http://live.gnome.org/Gedit/LaTeXPlugin](http://live.gnome.org/Gedit/LaTeXPlugin) ?

> 
How do I install the plugin?

First of all download the latest release of the plugin. It contains a folder and a file that you have to copy to ~/.gnome2/gedit/plugins, where ~ is your home directory. You may have to create gedit/plugins if you haven't installed any plugins, yet. After that you may restart gedit and activate the plugin in the settings dialog.

---

### Post by wannabegeek on 2009-10-02
thanks Xcan, will try and repost...

---

### Post by jeneverboy on 2009-10-02
Hi,

First of all I use LaTeX a lot, its most useful for making formulas.
I wondered if the automatic package updates work in UBUNTU, cause I had some problems there.

If you want to check if a package is installed use:

```
aptitude show [COLOR="Red"]yourpackage[/COLOR]
```

BYe

---

### Post by ad_267 on 2009-10-02
I'll just add that in order to use the gedit LaTeX plugin you need to install the rubber package from synaptic/apt-get.

+1 to the LaTeX wikibook and Kile is also another good LaTeX editor.

---

### Post by XCan on 2009-10-02
Well, it is rather straight forward to change the builds to not use rubber anyway if one doesn't like to use it (like me). :)

---

### Post by Stefan_K on 2009-10-02
> **ad_267 said:**
> +1 to the LaTeX wikibook and Kile is also another good LaTeX editor.

I also recommend [Kile]("http://kile.sourceforge.net/"), I'm using it since a long time and I'm very satisfied with it. Installing it would bring some kde libs to the system, but they didn't bother me at all.
My second choice would be Texmaker, then perhaps gedit, the standard text editor. Gummi is new, perhaps not really stable or well-developed.
TeXworks is another new editor, there could be a package for Ubuntu now, at least it can be used as [application bundle]("http://www.appbundles.org/").

Stefan


--
[TeXblog]("http://texblog.net")

---

### Post by Chronon on 2009-10-02
I've been using geany on my netbook.  It works well, has a keyboard shortcut for compiling, etc.

---

### Post by wannabegeek on 2009-10-03
This is a very noob ?..... when XCan wrties, 

"you have to copy to ~/.gnome2/gedit/plugins, where ~ is your home directory."

I am having trouble finding this location...I am reading about the file structure as I am still getting used to it, but could use a hint about the exact path...

thanks so much, everything I do now is a small battle....

wbg

---

### Post by ad_267 on 2009-10-03
You might need to create that directory. And directories beginning with a "." are hidden, so click on "View" - "Show hidden files" in the file browser. The full location for me is: /home/adam/.gnome2/gedit/plugins

---

### Post by wannabegeek on 2009-10-03
hidden, I suspected or not there.....it's hard to know which when not sure of path.. :)

I used ls -a and didn't them...i was skeptical however, b/c I have some other plugins that 
probably came with the installation.

I finally got the folder and loader file in the right place....it shows up in gedit's plugin window,
however, the plugin is grayed out and the error: cannot read contents of file GeditLaTeXPlugin
show in terminal

peace,

wbg

---

### Post by ad_267 on 2009-10-03
Ok well for starters check that all the files are in the right place. This is the contents of my ~/.gnome2/gedit/plugins (minus all the other plugins):

Directory: GeditLaTeXPlugin
File: GeditLaTeXPlugin.gedit-plugin

Then in ~/.gnome2/gedit/plugins/GeditLaTeXPlugin I have all this:
```
bibtex.xml                     __init__.py        latex.xml        templates
ChangeLog                      __init__.pyc       listings.xml     tools.xml
COPYING                        INSTALL            preferences.xml  util
GeditLaTeXPlugin.gedit-plugin  install.sh         snippets.xml
glade                          install-system.sh  src
icons                          latex.pkl          symbols.xml
```

---

### Post by wannabegeek on 2009-10-04
Hi again, I got .....I didn't have my directories setup quite right....

Thanks a ton to all for their help, it's great to have such explicit examples in the beginning...this is like a working with a new math for the first time, I just need to make it work out, then the understanding comes with lots of repetition...

---

