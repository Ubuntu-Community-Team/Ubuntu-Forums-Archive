---
title: "Question on running multiple copies (not instances) of a program (Firefox, Songbird)"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by Andy06 on 2009-07-01
This is sort of a Firefox 3.5 question but not really to do with how to get it or when it will be updated so please read on :P

I have on my computer, FF v3.0.11. Then I installed the tar.gz archive from Mozilla for the latest FF v3.5 and extracted and placed the "firefox" folder in my home directory. Now I can run FF v3.5 alongside FF v3.0.11 as it has not replaced it.

At this stage I have 2 questions:

1. Is this new FF v3.5 install self contained since it is operating out of a folder? Or is it operating out of a folder?

2. When I run this "self-contained" version, it accesses my old FF v3.0.11 profile in the "firefox" folder of .mozilla. So I guess it is not completely self contained, does it access anything else apart from profiles outside of its own folder? I would have thought that a self contained directory would have its own profile folder.

Now I was feeling adventurous, so I installed the Firefox 3.5 beta fromt he repos as well ;) (Oh and I also have swiftfox installed btw, in addition to Opera, Epiphany, Galeon, Fennec, Midori.....yeah I'm a browser whore but I digress...).
So now this new complete install of FF v3.5b4 works well also but has its own profile that it created in the "firefox 3.5" folder in the .mozilla folder in the home directory.

At this stage I have 2 more question:

1. What happens when the complete install of FF v3.5b4 is updated to the full version, will it still maintain a separate install? I ask because in windows you could install all the betas alongside the v3.0 install but you cannot do that for the full 3.5 version, it overwrites your older 3.0 install. Will this happen on Ubuntu as well?

2. Is there any disadvantage to running a self contained install fromt he .tar.gz package apart from the fact that I won't get updates (or will I?), I quite like the idea of an entire app and all its support files in one single directory. I think that's the way all apps should be in all OSes, so that when you delete the directory, nothing gets left behind and there is nothing to uninstall. 

The no updates thing from a tar.gz could actually be an advantage and not a drawback since you will get instant updates from Mozilla directly instead of having to wait for the repos to be updated.

Thanks a lot.

---

### Post by The Cog on 2009-07-01
It's filthy browser whores like you that give browsing a bad name. Your mother would be appalled.

1:
Yes, the firefox from the repos will remain separate because it's in a different place, somewhere in /usr/share. The windows installer probably doesn't give you an option where to put it, but of course, you can unzip a tarball wherever you like. I put all mine in /opt in suitably named folders.

2:
No other major disadvantages that I can think of in this case. 

Sometimes the downloaded binaries need different libraries installing, e.g. for earlier firefox binaries (and still for the sunbird binary from mozilla) I have to install libstdc++5 whereas the Ubuntu repo versions have been rebuilt against the Ubuntu library files, libstdc++6. 

They will all try to use your settings in ~/.mozilla, potentially leading to ugly settings conflicts between versions, but I guess you already know that.

---

### Post by Andy06 on 2009-07-01
Hey Cog,

Yeah, I am very promiscuous with my browsers. I even have Flock, Chrome, Maxthon, IE8, Opera 9.64, Opera 10 beta, Fennec plus some more obscure ones on Windows. And of course Firefox to actually browse the net.

AFAIK, the "self contained" tar.gz is messing with the profiles in "firefox" folder in .mozilla. The Shiretoko beta created a nice new "firefox 3.5" folder for its profiles in .mozilla so that is separate. What I am wondering is, will the update to the full 3.5 delete that new folder and resume working with the "firefox" folder as would normally be expected?

Currently my .mozilla has Songbird, Firefox, Firefox 3.5 and Sunbird folders.

There is really no end to my debauchery since now I am going to install Swiftfox RC3 and the Windows version of FFv3.5 on Wine. That will give me 6 firefoxish browsers to play with and compare (FFv3.0.11, FFv3.5 tar.gz, FFv3.5b4 full install awaiting update, FFv3.5 on Wine, Swiftfox 3.5RC3 and Epiphany) :mrgreen:

---

### Post by Andy06 on 2009-07-01
Oh no....Swiftfox installed but does not show up in synaptic. How do I get rid of it?

---

### Post by The Cog on 2009-07-02
> **Andy06 said:**
> AFAIK, the "self contained" tar.gz is messing with the profiles in "firefox" folder in .mozilla. The Shiretoko beta created a nice new "firefox 3.5" folder for its profiles in .mozilla so that is separate. What I am wondering is, will the update to the full 3.5 delete that new folder and resume working with the "firefox" folder as would normally be expected?

That sounds odd to me. I don't think any of the betas I tried made a ~/.mozilla/Firefox3.5 folder. I'm sure the real 3.5 (downloaded from the mozilla site) doesn't do that. It continues to use ~/.mozilla/firefox. If I ever had a separate 3.5 folder, it's gone now. I do remember repeatedly restoring .mozilla from a tar file after the betas mucked up my 3.0 settings, which implies they both used the same folders/files. I would suggest that you make a backup of the .mozilla folder before trying things out. Perhaps you could have lots of different folders, and have a launcher script that changes a symlink from .mozilla to the right folder immediately before launching the relevant version browser.

If swiftfox installed from the repos, then it _must_ be there in synaptic (mustn't it?). If you can't find it, maybe just not worry about it and leave it there - I don't know. It'll all be gone after the next full install anyway. I always install rather than upgrade to make sure I get rid of the cruft.

---

### Post by Andy06 on 2009-07-02
Ok this is wierd.

Re:Swiftfox,

It does not show up in the default synaptic view which is sections>ALL in the left pane. but then if I go and change the classification to status and category to installed (local and obsolete), it shows swiftfox-prescott along with all the other apps I have installed using .debs.

More weird is the fact that quicksearching using the snaptic search bar brings up nothing, not even when I have the status>installed pane open (which has only 9 apps/listings). BUT if instead of using the search bar, I manually click on the search icon (the binoculars) and then attempt to search, it finds it successful.  

Re:Shiretoko,

Yea it definitely created a Firefox 3.5 folder in the .mozilla directory. I checked using profile manager. Are you sure it hasn't for you? Because this is normal behaviour for windows versions of the beta so that you could try them without messing up with your default v3.0 install. I'm wondering if the folders will converge with the full v3.5 version though.

---

### Post by The Cog on 2009-07-02
> **Andy06 said:**
> Yea it definitely created a Firefox 3.5 folder in the .mozilla directory. I checked using profile manager. Are you sure it hasn't for you? Because this is normal behaviour for windows versions of the beta so that you could try them without messing up with your default v3.0 install. I'm wondering if the folders will converge with the full v3.5 version though.
Well, like I say, I kept restoring a backup of /mozilla after trying out the betas, so maybe at some stage they did and I didn't notice.

---

### Post by Andy06 on 2009-07-06
If I keep FFv3.0.11, it will update to 3.5 right by replacing it?

What if I keep FFv3.0.11 and keep Shiretoko 3.5b4 installed as well, which one will update? Will it update the beta instead and let me have two full fledged FF installs?

When will FFv3.5 be available in the repos btw?

---

