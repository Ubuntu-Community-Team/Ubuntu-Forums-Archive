---
title: "Remove all traces of Firefox and install cleanly, How to?"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by LewRockwellFAN on 2011-02-24
I'd like to completely remove ALL traces of Firefox so I can do a complete reinstall. I tried uninstalling and reinstalling (2 separate steps) from Synaptic. My old screwed up profiles and bookmarks were still there. I went back to Synaptic and completely removed everything that had firefox in the description and then reinstalled. Same story. I did this again and then found and deleted every file and directory in my system containing either "firefox", "ubufox", or "mozilla" (except for a couple that were obviously only related to Thunderbird) as part of the name. Then I reinstalled and it STILL used one of my old profiles (and by Murphy's Blood it picked one of the most fscked up ones to keep!). Am I going to have to completely reinstall the whole system to get rid of all traces of Firefox so I can install it cleanly?  Not a big deal if I need to, but I'd like to understand this. 

As to WHY I want to do this, just in case it has relevance or someone is curious, 2 independent reasons:
1-I played around with font and color settings in multiple profiles and neglected to keep one unmodified. I assumed Firefox would have "restore defaults" button but it doesn't.
2-Something (malware presumably) was causing Firefox to start up with 2 tabs loading on.com and black.com instead of my home page. I checked the homepage settings both from edit, preferences and from about:config and it was set correctly. When I click the home icon it goes to the right page.

Last Minute Addendum:
OK, one more problem just discovered that might be related. The entire number pad on my keyboard seems to have quit working, not just in Firefox. Might be an unrelated hardware problem or might be further signs of malware of some sort.

If nobody tells me different in a few hours, I'm going to reinstall, cause this begins to look like a virus and last time I ran Clam it seemed to delete files without even asking which makes me leery of it. I've been banking on the greater inherent resistance of 'nixes plus the fact I don't install stuff without thought. Maybe that wasn't conservative enough.

TIA for any thoughts on any of this.

---

### Post by Foxheadz on 2011-02-24
```
sudo apt-get remove firefox
Sudo apt-get purge firefox
```

If that doesn't work, search your computer for all files associated with firefox and delete it.

---

### Post by cgroza on 2011-02-24
```

sudo apt-get purge firefox
sudo apt-get autoremove
sudo apt-get clean

```

---

### Post by uRock on 2011-02-24
With firefox closed, open your /home and delete the .mozilla folder. When you open Firefox it will create an all new profile.

---

### Post by LewRockwellFAN on 2011-02-26
@ Foxheadz, cgroza, & uRock:

Thanks for the ideas. As for uRock's suggestion, I **_think_** I already tried that but I suppose it is possible I neglected to shutdown Firefox before deleting the folder. I rebooted from an alternate boot partition in the 64 bit 10.04 Lucid and checked this thread without logging in. Number pad worked fine then so I saw that as confirmation that the problem with the kb was not hardware but that  there was something sufficiently messed up in the 32 bit 10.04 boot partition that reinstallation was advisable. But I was going to try all these ideas anyway as a learning exercise so I rebooted and selected the default grub option of booting into the 32 bit installation where I had these problems and it booted the 64 bit installation instead. I repeatedly rebooted to double check this and indeed selecting either the entry for latest version of the 32 bit or the entry for the latest version of the 64 bit*** both*** booted the 64 bit. So I was unable to attempt these fixes and had to reinstall.

So I guess the proper thing is to leave this thread marked unsolved for the moment in case anyone wants to comment on this weirdness and its possible causes and then mark it solved in a day or so since it kinda sorta is.

---

