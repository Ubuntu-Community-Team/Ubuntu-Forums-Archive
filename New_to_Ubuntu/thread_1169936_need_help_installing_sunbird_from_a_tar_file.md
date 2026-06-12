---
title: "need help installing sunbird from a tar file"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by Whatnotery on 2009-05-25
Ok I want to install Mozilla sunbird and I downloded the tar file to my desktop but I have no clue what to do from here. advice and/or a tutorial would be appreciated.

---

### Post by Mornedhel on 2009-05-25
Are you aware that Sunbird is available through the repositories ?

```
sudo apt-get install sunbird
```

---

### Post by Whatnotery on 2009-05-25
oh now I feel really dumb

---

### Post by Uzi304 on 2009-05-25
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

In the case of Sunbird however. Untar the file and cd to the extracted folder and type in ```
./run-mozilla.sh
```

Not entirely sure though

Haha and there's also the repos.

---

### Post by Didius Falco on 2009-05-25
> **Whatnotery said:**
> Ok I want to install Mozilla sunbird and I downloded the tar file to my desktop but I have no clue what to do from here. advice and/or a tutorial would be appreciated.

Welcome to the Ubuntu forums.

First, I'd like to point out that Sunbird is available in the Synaptic Package Manager (**System/Administration/Synaptic Package Manager**), and it will install it for you.

It's recommended that you, whenever possible, use the repositories. It installs it for you, pulls in any other files that the package depends on, etc. It also makes for a lot cleaner, easier uninstall or reinstall.

I'd _strongly_ suggest that you use the repositories.

That said, here is a link:

[http://ubuntuforums.org/showthread.php?t=54798](http://ubuntuforums.org/showthread.php?t=54798)

Regards,

Didius

---

### Post by Whatnotery on 2009-05-25
well I got it installed through the repositories but thanks for all the advice

---

### Post by Didius Falco on 2009-05-25
> **Whatnotery said:**
> well I got it installed through the repositories but thanks for all the advice

We are all glad to help. Don't feel dumb, btw - the only dumb question is the one you don't ask. Not even Linus Torvalds was born knowing this stuff. We all have to learn it...

Regards,

Didius

---

### Post by albinootje on 2009-05-25
Which Ubuntu release are you using ? Ubuntu Hardy has Sunbird 0.7, while Ubuntu Jaunty has Sunbird 0.9, that looks like quite a difference in user experience.

---

### Post by Whatnotery on 2009-05-25
> **albinootje said:**
> Which Ubuntu release are you using ?
I'm using jaunty

---

### Post by albinootje on 2009-05-25
> **Whatnotery said:**
> I'm using jaunty

Good, then you have a pretty recent Sunbird installed now. :)
See : [http://www.mozilla.org/projects/calendar/sunbird/](http://www.mozilla.org/projects/calendar/sunbird/)

---

