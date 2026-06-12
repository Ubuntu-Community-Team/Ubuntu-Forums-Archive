---
title: "Could not download all repository indexes &quot; HELLP!!&quot;"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by vlad1975 on 2009-10-03
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B4C340A1EDCA87CAFailed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.88.31 80]
Some index files failed to download, they have been ignored, or old ones used instea

Could someone tell me how to fix this please?

---

### Post by infinitejones on 2009-10-03
EDIT having read your initial post properly ;)

The "404 Not Found" at the end suggests that you've got the wrong URL for the repository it's trying to download. Exactly the same as if you type an incorrect web address into a browser. So double check what you copy-and-pasted into the Software Sources dialogue when you added the repository. 

It looks like "http://ppa.launchpad.net jaunty" is what you added, but that's not a complete URL.

---------------------------------------------------------------------------

From [this Ubuntu Forums thread]("http://ubuntuforums.org/showthread.php?t=1221323"):

[I]Type this command into the terminal ("Applications > Accessories > Terminal") sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys

And then add the hexadecimal numbers to the command...[/I]

What he means by the last line will be, in your case, B4C340A1EDCA87CA - the string of letters and digits in the error message. So you need to type/copy and paste:
```

apt-key adv --keyserver keyserver.ubuntu.com --recv-keys B4C340A1EDCA87CA
```

What you'll find with Ubuntu is that if you just copy and paste error messages into Google, you'll find the answer easily enough (and without having to wait for people to reply to forum posts!).

Unless you've got a really really bizarre error, the chances are someone else has encountered it previously, and fixed it too. Always worth checking Google first!

---

### Post by hal10000 on 2009-10-03
Try the ubuntu sources.list generator: [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by rustutzman on 2009-10-03
If you haven't made any changes it may be that the main us servers have been very slow. At least for me the last two days and not completing some refreshes. Keep trying. Mine eventually got them all updated.

Russ

---

### Post by vlad1975 on 2009-10-04
ok i think i found the what is giving the error.If you look at my screenshot. That seems the one that is giving the error when i try to remove it it does not remove. is there a manua way for me to remove it or typing something in terminal? coz once thats gone i thing i can put the proper lines in without anymore problem

---

### Post by vlad1975 on 2009-10-04
here is the screenshot

---

