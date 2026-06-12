---
title: "How do i get the apple type menu"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by axlandslash44x on 2009-05-18
Hi all,

I now have a basic but new theme which i like

But i would like to get the "apple style" menu at the bottom of the my screen

Can anyone help a newb do this?

Bare in mind I struggled getting a theme to work :)

Thanks

---

### Post by nolliecrooked on 2009-05-18
> **axlandslash44x said:**
> Hi all,

I now have a basic but new theme which i like

But i would like to get the "apple style" menu at the bottom of the my screen

Can anyone help a newb do this?

Bare in mind I struggled getting a theme to work :)

Thanks

The dock?

---

### Post by axlandslash44x on 2009-05-18
Sorry not to too sure on terminology..


Set of Icons.. I presume they can be anything.... and I think they get larger if you hover mouse over them

although not sure...


As per this image - which funny enough is the theme im using - with a slightly more manly image

[http://gnome-look.org/CONTENT/content-pre1/78633-1.jpg](http://gnome-look.org/CONTENT/content-pre1/78633-1.jpg)

---

### Post by ad_267 on 2009-05-18
Yes that's the dock. There's a few to choose from:

Avant Window Navigator (AWN)
Docky theme for Gnome-Do
Cairo dock
Kiba dock

AWN and Docky seem to be the two most popular. That screenshot looks like AWN.

---

### Post by emacbri on 2009-05-18
Hi,

Try googleing "Gnome Do". It's not exactly like the apple "dock" but it is the best "dock" for linux (In my opinion).:)

---

### Post by nolliecrooked on 2009-05-18
> **emacbri said:**
> Hi,

Try googleing "Gnome Do". It's not exactly like the apple "dock" but it is the best "dock" for linux (In my opinion).:)

its better than the Mac dick.

---

### Post by fabounet on 2009-05-19
this screenshot is Cairo-Dock2, with the weather and show-desktop applets.
(the best dock ever, if you didn't try it yet, it's time to do !)

---

### Post by ceciliaFX on 2009-05-19
> **emacbri said:**
> Hi,

Try googleing "Gnome Do". It's not exactly like the apple "dock" but it is the best "dock" for linux (In my opinion).:)
I just downloaded "Gnome Do" to try it out and unless I'm missing the point it requires that you type.

Now, I know linux folks like to type, but dispite the fact that I enjoy linux very much I hate typing. call me crazy :)

axlandslash44x: where did you get that beautiful theme??
I'm jealous!

I'm going to try AWN

---

### Post by ceciliaFX on 2009-05-19
> **fabounet said:**
> this screenshot is Cairo-Dock2, with the weather and show-desktop applets.
(the best dock ever, if you didn't try it yet, it's time to do !)
ok, you convinced me...I'll be looking at Cairo-Dock2

LOL

---

### Post by NESFreak on 2009-05-19
> **ceciliaFX said:**
> I just downloaded "Gnome Do" to try it out and unless I'm missing the point it requires that you type.

Now, I know linux folks like to type, but dispite the fact that I enjoy linux very much I hate typing. call me crazy :)

axlandslash44x: where did you get that beautiful theme??
I'm jealous!

I'm going to try AWN

go to the settings of gnome-do and change the theme to docky

---

### Post by raymondh on 2009-05-19
I use AWN.  Accessories > Terminal

```
sudo apt-get install avant-window-navigator
```

Here's a link for the AWN FAQ

[http://wiki.awn-project.org/FAQ](http://wiki.awn-project.org/FAQ)

Since were in the "apple look alike" topic, I also use mac fonts.  If you want to try.

Accessories > terminal (you may copy & paste and enter after each line)

```
wget http://ubuntu-debs.googlecode.com/files/macfonts.tar.gz
tar zxvf macfonts.tar.gz
sudo mv macfonts /usr/share/fonts/
sudo fc-cache -f -v
```

Then go to preference > appearance > tab and tweak to your liking.  My setting here are as follows:

Application > lucida grande 10
Document > lucida grande 10
Desktop > macgrande 10
Window Title > Lucida Macbold
Fixed Width > lucida console

On the details tab, my hinting is set to NONE and smoothing to SUBPIXEL (LCD)

Hope this helps.

---

### Post by ceciliaFX on 2009-05-19
> **ceciliaFX said:**
> ok, you convinced me...I'll be looking at Cairo-Dock2

LOL
I ended up installing using instructions from [here]("http://maketecheasier.com/how-to-install-and-configure-cairo-dock-in-ubuntu-intrepid/2009/01/20")

except the last command is:

sudo apt-get install cairo-dock cairo-dock-plug-ins

yes, I (oh, the horror), I used a terminal. but I just copied and pasted, so it wasn't so bad.  :)

looks interesting so far

---

### Post by ceciliaFX on 2009-05-19
> **NESFreak said:**
> go to the settings of gnome-do and change the theme to docky
it doesn't have that theme

---

### Post by NESFreak on 2009-05-19
> **ceciliaFX said:**
> it doesn't have that theme


Its available starting from version 0.8 i believe. If you're still running hardy or intrepid, there's a ppa available containing the latest version [http://do.davebsd.com/wiki/index.php?title=Installing_Do#Ubuntu](http://do.davebsd.com/wiki/index.php?title=Installing_Do#Ubuntu)

---

### Post by ad_267 on 2009-05-19
> **ceciliaFX said:**
> I ended up installing using instructions from [here]("http://maketecheasier.com/how-to-install-and-configure-cairo-dock-in-ubuntu-intrepid/2009/01/20")

except the last command is:

sudo apt-get install cairo-dock cairo-dock-plug-ins

yes, I (oh, the horror), I used a terminal. but I just copied and pasted, so it wasn't so bad.  :)

looks interesting so far

You know for all these "sudo apt-get install..." commands you can also use Synaptic Package Manager right? You usually don't actually have to use the command line for anything. And the docky theme for gnome-do transforms gnome-do into a dock, so you don't have to type at all.

---

### Post by ceciliaFX on 2009-05-19
> **ad_267 said:**
> You know for all these "sudo apt-get install..." commands you can also use Synaptic Package Manager right? You usually don't actually have to use the command line for anything. And the docky theme for gnome-do transforms gnome-do into a dock, so you don't have to type at all.
I tried that first, but it wasn't cooperating, so i went looking for another way.

it worked in any case

thank you

---

### Post by ceciliaFX on 2009-05-19
> **NESFreak said:**
> Its available starting from version 0.8 i believe. If you're still running hardy or intrepid, there's a ppa available containing the latest version [http://do.davebsd.com/wiki/index.php?title=Installing_Do#Ubuntu](http://do.davebsd.com/wiki/index.php?title=Installing_Do#Ubuntu)
thank you

---

