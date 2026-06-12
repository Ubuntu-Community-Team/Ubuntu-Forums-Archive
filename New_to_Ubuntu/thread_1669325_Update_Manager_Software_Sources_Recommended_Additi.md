---
title: "Update Manager Software Sources? Recommended Additional Repositories?"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by Flood-X on 2011-01-17
Hello everyone,

I have a question regarding the Update Manager in Ubuntu 10.10.

Under Settings there is a Tab for "Other Software." After my installation, there are two boxes checked off:
"Independent provided by third party software developers"
"Independent (source code) provided by third party software developers"

Above those two choices, there are two unchecked boxes:
"Canonical partners software packaged by canonical for their partners"
"Canonical partners (source code) software packaged by canonical for their partners"

Is it recommended to also check these two boxes off?

Also, what repositories should the average user add? Also, how do I go about doing that (if they aren't added by default in Ubuntu 10.10)?

---

### Post by DOSIX on 2011-01-17
you could check those off too. although you don't necessarily have to. as for adding repositories check out [this]("https://help.ubuntu.com/community/Repositories/CommandLine"). It is up to each user which repos they want to use, however.

---

### Post by Flood-X on 2011-01-17
Thank you a lot for your reply.

Could you explain what those repositories include or do?

---

### Post by Flood-X on 2011-01-17
sorry, my reply was posted 2x

---

### Post by mick222 on 2011-01-17
The partner repositories contain sun-java and other software  Plus some other stuff mainly flashplugin and adobereader. Open java works for most things but if you want sun java install this repo . Most people don't need the source repositories so you can disable these.
   As for other repositories thats up to you if you want install ubuntu tweakwhich makes it easy to add or remove the most popular repositories like google if you want chrome or google earth just dont go to mad or updating could take awhile

---

### Post by mikesmithv on 2011-02-25
> **mick222 said:**
> The partner repositories contain sun-java and other software

Another machine I have running 10.04 (lucid) cannot update the sun-java stuff like 10.10 does.  I noticed there is no built-in software source in 10.04 called:

"Independent provided by third party software developers"

Is there a way to manually add the sun-java software source to earlier Ubuntu version or do I have to upgrade to 10.10 for this?

---

### Post by Hakunka-Matata on 2011-02-25
[http://www.ubuntugeek.com/sun-java-moved-to-the-partner-repository-in-ubuntu-10-04-lucid.html]("http://www.ubuntugeek.com/sun-java-moved-to-the-partner-repository-in-ubuntu-10-04-lucid.html")

---

### Post by Hakunka-Matata on 2011-02-25
As far as which repositories to recommend I guess that depends on the user's requirements.  There are countless repositories available....

For what it's worth I include pictures of what I have installed:

---

### Post by mikesmithv on 2011-02-25
Your screenshot show 3 software source checked:

1. Conical Partners
2. Independent
3. Medibuntu

My problem is that the middle item "Independent" does not appear in the list in 10.04.  I think that might be a "built in" software source new to 10.10.

---

### Post by Hakunka-Matata on 2011-02-25
Yes, you may be correct, 10.10 refers to it as 'third-party' software sources too, I'm looking for the equivalent in 10.04, as I don't have a release 10.04 running right now.

---

### Post by Hakunka-Matata on 2011-02-25
> Third-Party Software Tab

Adding Canonical Partner Repositories

The "Third-Party Software" tab is where you will be able to add the Canonical Partner Repositories. You will see two Canonical Partner repositories listed - one for applications and another for source code (src). The partner repositories offer access to proprietary and closed-source software and are not enabled by default. Users must specifically enable these 'partner' repositories. Select "Close" and "Reload" to save and update the database if you chose to add either or both of them.

    *

      SoftwareSources-Partner.png 

CD-ROM/DVD

Other CD-ROM/DVD sources may be added on this tab. Click the "Add CD-ROM" button after inserting a CD-ROM containing packages. After adding the CD-ROM/DVD, it will be searched for packages during installation requests. 
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

the quoted bit shows up in the url listed above, is that a picture from 10.04?  If so, that might be 10.04's equivalent ????????

---

### Post by Hakunka-Matata on 2011-02-25
nope, I don't think that's the equivalent, if there is one?  My mistake

---

### Post by mikesmithv on 2011-02-27
Under Maveric the APT line for "Independent provided by third party software developers" is:

deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maveric main

Under Lucid I tried using the equivilent APT line:

deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) lucid main

But it doesn't work.  It results in a "file not found" message, so apparently there is no way to add sun-java as a software source under earlier version of Ubuntu.

---

