---
title: "Update manager W: GPG error: http://archive.canonical.com karmic Release: The followi"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by Habacuc on 2010-02-18
Hi I am really new to Ubuntu and I don't know what to do with this:
 When I am open the Update manager after loading the updates it displays this message:
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) karmic Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com> 
Does anyone have any idea on how to solve it?
Kind regards

---

### Post by zvacet on 2010-02-18
**Applications>accessories>terminal **

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by landrew on 2010-02-18
> **zvacet said:**
> **Applications>accessories>terminal **

```
sudo apt-get update && sudo apt-get upgrade
```

And when the "apt-get update" generates the same error (BADSIG: 40976..."), since the signature is still bad, then what?  It seems that you need to update a signature to solve the problem...

-L'andrew

---

### Post by plucky on 2010-02-18
> **landrew said:**
> And when the "apt-get update" generates the same error (BADSIG: 40976..."), since the signature is still bad, then what?  It seems that you need to update a signature to solve the problem...

-L'andrew

This [link](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html) might help

Good Luck

---

### Post by landrew on 2010-02-18
> **zvacet said:**
> **Applications>accessories>terminal **

```
sudo apt-get update && sudo apt-get upgrade
```

Hi folks - problem solved.  The above did NOT work to resolve the problem (since that's where I was seeing the problem).  What did work was Solution #2 from the link that plucky provided.  I first tried blowing away the /var/log/apt/lists directory and letting it try again, but that didn't work (same BADSIG error).  The following solved the problem for my install:

```

sudo aptitude -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update
sudo apt-get update && sudo apt-get upgrade

```

The system seeing this problem is behind a web proxy at work, so it is possible that there were some cache-related errors.  As it's been working fine for weeks before this failure, I'm not sure if there's a "BrokenProxy" or not, but this did resolve the problem (and normal "apt-get update && apt-get upgrade" commands work now.)

Thanks for the fix (and the really fast responses) folks.

---

### Post by Habacuc on 2010-02-18
Hi Fellas! Thank you for your fast answers, sadly neither of them have solved my problem yet. DOes anyone know what else could be done?

---

### Post by plucky on 2010-02-19
> **Habacuc said:**
> Hi Fellas! Thank you for your fast answers, sadly neither of them have solved my problem yet. DOes anyone know what else could be done?

From **System > Administration > Software Sources** try a "Download" from a different server to see if that fixes the problem.

Good Luck

---

### Post by Habacuc on 2010-02-21
> **plucky said:**
> From **System > Administration > Software Sources** try a "Download" from a different server to see if that fixes the problem.

Good Luck
It seems to be that the problem is still unsolved. I have tried this solution you posted. What else could be? 
Kind regards 
Habacuc

---

### Post by landrew on 2010-02-22
> **Habacuc said:**
> It seems to be that the problem is still unsolved. I have tried this solution you posted. What else could be? 
Kind regards 
Habacuc

I did a bit more reading on this, even though using the No-Cache and BrokenProxy options seems to have fixed my problem.  This appears to be a long-running bug, as shown in:

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24234](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24234)

If you check out bug report entries #50 and #60, there are some tips there that might help out.  The tips in entry #50 are pretty much the same as the others in this thread, except for making sure that the source repositories are the main repositories (which are probably still going to transparently redirect - but maybe not.)

I haven't tried (or even looked too closely at) the script in entry #60, but that appears to be checking and redownloading any missing or non-functional keys for repositories that you are using.

In any case, this does seem to be a continuing problem, and if you read through that bug report (assuming you are interested in all the "under the hood" info), it seems that occasionally, some mirrors get out of sync with the main repositories, causing this problem.

I haven't yet read the definitive solution to this, other than perhaps repeating the above solutions after a day or so (giving repository mirrors a change to get their files updated, in case you keep hitting the same mirrors.)

Best wishes, and here's hoping for a real fix, since this shouldn't be a normal occurrence. 

-Andrew

---

