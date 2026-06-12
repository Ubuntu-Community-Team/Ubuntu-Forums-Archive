---
title: "How do I get shinier looks in Ubuntu?"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by Uubnewb on 2009-02-01
Hi everyone,

I've been using Windows Vista Ultimate for quite a while before I recently installed Ubuntu 8.10. One thing that Vista Ultimate has that I'm rather fond of is the whole glossy/glass/transparent thing it's got going (see screenshot).

Is there any way to mimic this look, especially the window's borders, in Ubuntu 8.10? I am using Compiz, but if there is anyting else I can use please let me know.

Also if it is not too much trouble would you mind putting the steps I need to follow here. No need to go into too much detail (ie use colour #[code]) juste tell me where to go (ie Settings>[somethin]>[something]}.

Any and all help will be greatly appreciated.

---

### Post by tegnoto89 on 2009-02-01
You could try the KDE desktop environment.  Definitely shinier, definitely more vista-y.

```
sudo apt-get install KDE
```  (I THINK that's the command)

Google image kubuntu (which uses the KDE desktop) and see if you like what you see.

---

### Post by CLomax on 2009-02-01
> **tegnoto89 said:**
> You could try the KDE desktop environment.  Definitely shinier, definitely more vista-y.

```
sudo apt-get install KDE
```  (I THINK that's the command)

Google image kubuntu (which uses the KDE desktop) and see if you like what you see.

sudo apt-get install kubuntu-desktop

---

### Post by tegnoto89 on 2009-02-01
> 
sudo apt-get install kubuntu-desktop


Thanks- I was kind of close!!  :-D

---

### Post by Ben Page on 2009-02-01
If you like pretty and glossy, and many themes and that kind of stuff, then download Ubuntu interpid ibex Ultimate edition 2.0. This edition has all sorts of stuff for customizing and much more already preinstalled. Its Ubuntu on steroids ;).

---

### Post by overlord.gaurav on 2009-02-01
You can find a guide on [this page]("http://tuxenclave.wordpress.com/2007/11/23/ubuntu-customization-guide-v2/") to do that.[Scroll down on the page to find the guide for Vista customization]

---

### Post by gjoellee on 2009-02-01
Install KDE 4.2.0 to your KDE or Kubuntu installation: [http://www.kubuntu.org/news/kde-4.2](http://www.kubuntu.org/news/kde-4.2)

---

### Post by ChildOfMana on 2009-02-01
No need to install KDE just to change the way your windows look.

Go to [www.gnome-look.org](www.gnome-look.org) and pick a theme.

There are a few that are made to mimick Vista, plus plenty more besides.

You will probably be wanting an emerald theme for your window borders, and a matching GTK theme for everything else.

Instructions are on the site but post back here if you need any additional help.

---

### Post by gjoellee on 2009-02-01
> **CLomax said:**
> sudo apt-get install kubuntu-desktop

I think you would get slightly better performance using just KDE and not Kubuntu.

NOTE: [www.kde-look.org](www.kde-look.org) is better for you then GNOME look if you use KDE

---

### Post by Bölvaður on 2009-02-01
> **CLomax said:**
> sudo apt-get install kubuntu-desktop

uh you forgot to tell him/her that you pick to log into kde or gnome from the login screen under "Session".

Also check out Emerald, which you can find under synaptic and probably in add/remove. Emerald can be pretty useful and make the boarders... well just try it out add and remove buttons like minimize, shade, pin....

GNOME
[http://www.gnome-look.org/](http://www.gnome-look.org/)
[http://art.gnome.org/](http://art.gnome.org/)

KDE
[http://www.kde-look.org/](http://www.kde-look.org/)

kiro dock and AWN (avant window navigator) can be useful. Search for "Avant" under add/remove

For more shiny things... uh find multi mouse and keyboard kernel, compile it and connect some fun stuff to your computer ;)


Im on the other hand more into awesome atm which is intensively lightweight and probably in your view not good looking. But when you get more away from the eyecandy and more into usefulness tiling window managers could be the way to go :popcorn:

---

### Post by mcduck on 2009-02-01
> **ChildOfMana said:**
> No need to install KDE just to change the way your windows look.

Go to [www.gnome-look.org](www.gnome-look.org) and pick a theme.

There are a few that are made to mimick Vista, plus plenty more besides.

You will probably be wanting an emerald theme for your window borders, and a matching GTK theme for everything else.

Instructions are on the site but post back here if you need any additional help.

+1 for this. All desktop environments are very configurable and can be made to look like almost anything. There's absolutely no reason to switch to other DEs just to change how your desktop looks like.

For Gnome, [http://gnome-look.org/]("http://gnome-look.org/") is a great place to get new themes.

To get transparent Window borders you most likely want to install Emerald (additional Window Decorator for Compiz (the "Desktop Effects") that has lots of transparent themes available.

All the other things you wanted can be done easily with Gnome's themes and Compiz plugins.

---

### Post by xCel on 2009-02-01
I've installed Emerald, Downloaded the theme, imported it emerald, but, how to I activate it!? 

Thanks :)

---

### Post by mcduck on 2009-02-01
> **xCel said:**
> I've installed Emerald, Downloaded the theme, imported it emerald, but, how to I activate it!? 

Thanks :)

you might have to run "emerald --replace" in a terminal or the Run-dialog (press Alt-F2 to open it) before the new window decoration theme is loaded.

Also, if you haven't done that already, you should probably install Compizconfig-Settings-Manager which allows more detailed configuration of desktop effects.. After you have that, open it and got ot Effects/Window Decoration, and change the command from "/usr/bin/compiz-decrator" to "/usr/bin/emerald" to make Compiz use Emerald as the default decorator.

---

### Post by SunnyRabbiera on 2009-02-01
But honestly if you use a computer for the bling I personally dont think you should use a computer...
Granted the default looks of Ubuntu may not appeal to everyone but I dont think looks should matter.
Now there are themes out there that can make ubuntu look like anything you want but keep in mind you probably wont get all the dressing windows offers.
But some themes look better then others.
Installing KDE for a Vista like look is a good suggestion, but its up to you if you want an entirely different interface and install all the packages.

---

### Post by XanTrax on 2009-02-01
If you want emerald to run by default, you can do one of two things.

Open CCSM (Compiz Configuration Settings Manager) and go to Window Decorations section and change gtk-window-decorator (or whatever) and replace that with emerald --replace.

Or

You can go to System (at the top) -> Preferences -> Sessions -> Login Tab (or something like that) and add a new entry.  In the "command" part just place 

emerald --replace

And then save it all and exit those screens. Now whenever you login, whatever window decorator is on by default will be replaced by emerald

---

### Post by Uubnewb on 2009-02-01
Wow!  Thanks for the great help guys, this is really awesome!:D

---

### Post by leonardo_neo on 2009-02-01
> No need to install KDE just to change the way your windows look.

Go to [www.gnome-look.org](www.gnome-look.org) and pick a theme.

There are a few that are made to mimick Vista, plus plenty more besides.

You will probably be wanting an emerald theme for your window borders, and a matching GTK theme for everything else.

Instructions are on the site but post back here if you need any additional help.
__________________


Agree with you,

To have better looks, one need not to switch to KDE.

---

### Post by xCel on 2009-02-01
OK, now I installed a theme with Emerald, but I want to remove it. I deleted it, but the buttons still stay the way they had it. I tired emerald --replace and still stayed. Any suggestions? :D

---

### Post by mcduck on 2009-02-01
> **xCel said:**
> OK, now I installed a theme with Emerald, but I want to remove it. I deleted it, but the buttons still stay the way they had it. I tired emerald --replace and still stayed. Any suggestions? :D

If you mean window frames then run "gtk-window-decorator --replace" to return to the default Compiz decorator that uses Metacity's themes.

---

### Post by HotShotDJ on 2009-02-01
> **ChildOfMana said:**
> No need to install KDE just to change the way your windows look.Agreed.  I've got all kinds of transparency effect with a stable, gnome desktop -- tango icons, custom Applications menu icon, transparent panel, transparent menus, transparent window borders, etc.

I just tweaked things using the Configuration Editor and CompizConfig Settings Manager.

Remember, whether you are using Gnome, KDE, or some other desktop environment, the "look & feel" of your desktop is almost infinitely customizable.  Don't like the icons?  Change them.  Don't like the Window Decorations?  Change them.  Don't like the panel? Menus? Wallpaper? Transparency? Bling?  Change them all!

---

### Post by Uubnewb on 2009-02-02
I've decided to stick with Gnome.  At the moment I'm using emerald, but every time I log into Ubuntu I have to type emerald --replace.  Is there a way to load the emerald theme automaticly at start-up?

---

### Post by dESAI on 2009-02-02
> **Uubnewb said:**
> Hi everyone,

I've been using Windows Vista Ultimate for quite a while before I recently installed Ubuntu 8.10. One thing that Vista Ultimate has that I'm rather fond of is the whole glossy/glass/transparent thing it's got going (see screenshot).

Is there any way to mimic this look, especially the window's borders, in Ubuntu 8.10? I am using Compiz, but if there is anyting else I can use please let me know.

Also if it is not too much trouble would you mind putting the steps I need to follow here. No need to go into too much detail (ie use colour #[code]) juste tell me where to go (ie Settings>[somethin]>[something]}.

Any and all help will be greatly appreciated.

Enable the reflection plugin for Compiz Fusion. You can also install themes for Emerald.

---

### Post by dESAI on 2009-02-02
> **Uubnewb said:**
> I've decided to stick with Gnome.  At the moment I'm using emerald, but every time I log into Ubuntu I have to type emerald --replace.  Is there a way to load the emerald theme automaticly at start-up?

I have a new installation of U-8.10 and Emerald starts automatically... I did not have to do anything for it I think.

---

### Post by mcduck on 2009-02-02
> **Uubnewb said:**
> I've decided to stick with Gnome.  At the moment I'm using emerald, but every time I log into Ubuntu I have to type emerald --replace.  Is there a way to load the emerald theme automaticly at start-up?
OPen CompizConfig Settings Manager (instal it if you haven't done that yet), then go to Effects/Window Decoration and change the command from"/usr/bin/compiz-decorator" to "/usr/bin/emerald".

Now Compiz will use Emerald by default. :)

---

### Post by Uubnewb on 2009-02-02
> **mcduck said:**
> OPen CompizConfig Settings Manager (instal it if you haven't done that yet), then go to Effects/Window Decoration and change the command from"/usr/bin/compiz-decorator" to "/usr/bin/emerald".

Now Compiz will use Emerald by default. :)

Ah!  That worked, thanks.

---

### Post by Jynxx on 2009-02-02
What is Emerald?

---

### Post by Uubnewb on 2009-02-02
> **Jynxx said:**
> What is Emerald?

Emerald is a desktop customizer.  It allows you to install certain themes and customize them quite nicely.

---

### Post by Jynxx on 2009-02-02
I'm playing with Emerald now. Once I import the theme, how do I apply it so that it takes effect?

---

### Post by Uubnewb on 2009-02-02
OK, I've only got two problems left.

The blurry border around my windows is supposed to go all the way around, but for some reason it doesn't always cover the top and bottom.  Check out the screenshot, and you'll see what I mean.  In this screenshot the small window in the center has the green blurry border all the way around, but the big window behind it does not.

The second problem is regarding Emerald, although this time it's not a big deal.  Sometimes when I'm in Emerald my CPU usage on one CPU briefly goes up to 100% causing Emerald to freeze for a few seconds before I can continue using Emerald.  Note that this is only while I'm in the Emerald theme manager, it does not affect my desktop or any other program I'm running.

Thanks for all the great help people.

---

### Post by Le-Dart on 2009-02-02
[http://www.gnome-look.org/content/show.php/Broken+Vista+GDM+Theme?content=95049](http://www.gnome-look.org/content/show.php/Broken+Vista+GDM+Theme?content=95049)

---

### Post by mcduck on 2009-02-02
> **Jynxx said:**
> What is Emerald?

Emerald is alternative Window Decorator for Compiz (the "Desktop Effects" in Ubuntu). It can be used for more flashy window border themes, and includes a graphical tool for creating & editing more window border themes.

To tell Compiz to use Emerald as decorator press Alt-F2 and run "emerald --replace".

To get back to the default decorator (which uses Metacity themes, originally made for Gnome's own window manager Metacity) press Alt-F2 and run "gtk-window-decorator --replace"

Of course you need to have Compiz running ("Desktop Effects" enabled) for this to work.

---

