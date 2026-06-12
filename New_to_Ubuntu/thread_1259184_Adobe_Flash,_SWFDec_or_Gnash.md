---
title: "Adobe Flash, SWFDec or Gnash"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by sourav123 on 2009-09-06
There are presently the above threee solutions for playing flash video. I am presently using SWFDec, but would like to know what are the limitations of not using Adobe's plugin.

I know that SWFDec is not the best there, but still I prefer free programs, so just like to understand what will I be missing. For the record, I mainly use Youtube and a handful of others video sites.

---

### Post by duanedesign on 2009-09-06
I am all for the open-source free alternatives, but i have never had much luck with the non Adobe Flash plugins. The only way you are going to know is to install one and try it. Start with swfdec-mozilla, if you find it buggy try mozilla-plugin-gnash. If none of the open source options work and you can stomach it then use the flashplugin-nonfree. I applaud your efforts to stick with open source.

I can tell you that the adobe plugin has worked great.

If you do decide to install the Adobe plugin, make sure you get rid of all the others or they may cause conflicts.

```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

---

### Post by Bucky Ball on 2009-09-06
> **duanedesign said:**
> 

```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

Good advice, but you can actually run one big command to remove everything:

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash adobe-flashplugin flashplugin-nonfree
```

:)

---

### Post by eyeyoubin on 2009-09-06
I'm using Jaunty and I've been having problems with Google street view (while youtube and other things were working) I was using swfdec. I tried flash-nonfree, no luck. I got rid of swfdec and flash. I then installed Gnash and everything works fine.

---

### Post by lasleym on 2009-10-02
I tried SWFDec + others, everythign worked fine except Streetview.  I found this fix on Google's help forum:





 
  Ubuntu uses open source software when possible, and the swfdec flash player that is used by default is not compatible with some flash, like street view.

1. Go to System>Administration>Synaptic Package Manager.  

2. Search (click the binoculars) for "flash."  

3. Mark for complete removal anything with swfdec in the title or description.

4. Mark for installation the adobe-flashplugin package.

5. Restart Mozilla.

**It worked for me**!:KS:KS

---

### Post by Tibuda on 2009-10-02
> **lasleym said:**
> Ubuntu uses open source software when possible, and the swfdec flash player that is used by default is not compatible with some flash, like street view.
It is not used by default. It is just the first option.

---

### Post by anelephant on 2009-10-14
I do belive that swfdec-mozilla is better as of now, but however it is not beeing developed as much as gnash wich got a new version  2009-09-23, and a second release earlier this year. Compare that to swfdec wich hasn't (at least to my knowledge) had any changes in 2009.

I think that gnash will with time be the default on linux platforms.

---

### Post by ZootHornRollo on 2009-10-16
Thank you.

Fixed my problem.



> **duanedesign said:**
> I am all for the open-source free alternatives, but i have never had much luck with the non Adobe Flash plugins. The only way you are going to know is to install one and try it. Start with swfdec-mozilla, if you find it buggy try mozilla-plugin-gnash. If none of the open source options work and you can stomach it then use the flashplugin-nonfree. I applaud your efforts to stick with open source.

I can tell you that the adobe plugin has worked great.

If you do decide to install the Adobe plugin, make sure you get rid of all the others or they may cause conflicts.

```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

---

### Post by Bucky Ball on 2009-10-16
Please mark thread as solved to help others. :)

---

