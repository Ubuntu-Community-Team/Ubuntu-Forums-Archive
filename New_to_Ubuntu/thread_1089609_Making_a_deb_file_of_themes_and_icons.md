---
title: "Making a deb file of themes and icons"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by rednick on 2009-03-07
Hi.

After a disaster with the Jaunty alpha, I'm now back on Hardy Heron.
It works so well and I've since installed it on my PC at work.

Having seen the results, several others want in and so I think there will be a few Hardy installs in our office in the near future :)

The thing is, I have over time modified my theme and icons to the extent that I now have an icon I'm happy with for absolutely everything, stolen from a hotch-potch of different icon themes found at Gnome-look.org, all in one folder and with an index.theme file.  I have also modded the moomex-ultimatum theme from Gnome-look to give a colour scheme to match the office decor and fit with company branding (yes I am a saddo!)

What I'd like is just to put a deb file on the network drive which other users can download.  A double click would then extract the icons and the theme files to the relevant directories and automatically configure GNOME to use the themes.

What I need to know is

1) Is this possible?

2) What files would the deb file need to contain? Would the contents of the hidden folders .icons and .themes cover it? The former contains one folder called rednick containing my icon graphics and index.theme, whereas the latter contains 2 folders called moomex-ultimatum and rednick, one containing the original theme and gtk, metacity and totem foldeers, and one containing my modified theme file.

3) How would one automate configuration to use the new theme and icons?

4) What app would I use to build it all up in a deb file.

Any pointers would be greatly appreciated.
Cheers
Nick

---

### Post by Toxicity999 on 2009-03-07
While this is completely possible, this is not really a good use of installer packages. Personally, I would just back up .themes and .icons in your home directory and call it good. Even make a tar if you so please. Just upload that to your intended place with a note explaining where to extract it, or where to move the files to. Easy.

---

