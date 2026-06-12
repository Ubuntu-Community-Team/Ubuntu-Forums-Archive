---
title: "Thunderbird calendar not working in Karmic"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-11-12
Cannot get the TB calendar to sync with Google Calendar in Karmic...it was working perfectly in Jaunty. Have installed the latest lightning and the latest provider.

---

### Post by cybergalvez on 2009-11-12
> **dunbrokin said:**
> Cannot get the TB calendar to sync with Google Calendar in Karmic...it was working perfectly in Jaunty. Have installed the latest lightning and the latest provider.

works for me, are you getting any error messages?

---

### Post by dunbrokin on 2009-11-12
No error messages....

File/New/Calendar is greyed out and I cannot enter any data for today...or any other day either.

---

### Post by borgvall on 2009-11-12
Check if you have libstdc++5 installed. It's required by Lightning. In Karmic libstdc++5 was replaced by libstdc++6 which is incompatible with Lightning.

---

### Post by dunbrokin on 2009-11-12
> **borgvall said:**
> Check if you have libstdc++5 installed. It's required by Lightning. In Karmic libstdc++5 was replaced by libstdc++6 which is incompatible with Lightning.

This package is no longer available.

---

### Post by XCan on 2009-11-12
Perhaps you could get it directly from [http://packages.ubuntu.com/jaunty/libstdc++5?](http://packages.ubuntu.com/jaunty/libstdc++5?)

---

### Post by dunbrokin on 2009-11-12
I imagine that TB will get around to sorting it out some time soon.....I hope!!

---

### Post by roalt on 2009-11-15
> **dunbrokin said:**
> I imagine that TB will get around to sorting it out some time soon.....I hope!!

Has there been a bug report filed already? If not, what's the best place to file it?

---

### Post by dunbrokin on 2009-11-26
The answer is to download Lightning from the Ubuntu Repository and not from the TB website.....works now.

---

### Post by iMacUser on 2009-12-08
After applying security and bugfix updates to Kubuntu 9.10 this morning, I can no longer view existing calendars, add new or do any calendar activity - menu options are greyed out.

I'm using Lightning 0.9 (installed from repositories, not Mozilla), Thunderbird 2.0.0.23.

Has anyone else experienced this problem today?

Thanks.

---

### Post by gdonwallace on 2009-12-08
I am currently running the release candidate for TB 3 and the latest lightening build and do not have any problems.

Both are very stable, as I am using TB 3 as my mail client on my work machine.  Have not had any problems.

Might suggest giving that a try.  The final release of TB 3 and Lightening should be coming out pretty soon.

---

### Post by iMacUser on 2009-12-09
Thanks gdonwallace, I've downloaded the just released Thunderbird 3.0 from Mozilla's website and installed the 8 December nightly build of Lightning.

Both seem to be working a treat.

---

### Post by roalt on 2009-12-10
I have thunderbird 2.0.0.23 running now with lightning 0.9 and provider for google calendar 0.5. Removing the manually installed 'Add On' and only installing them from [B]synaptic package manager
[/B] did the trick.

---

### Post by kngharv on 2010-01-04
> **roalt said:**
> I have thunderbird 2.0.0.23 running now with lightning 0.9 and provider for google calendar 0.5. Removing the manually installed 'Add On' and only installing them from [B]synaptic package manager
[/B] did the trick.


Same here.  in my case, I didn't bother with libstdc++5.  All I did was install the lightning extension from repository and it worked.

I don't like the way how this problem is resolved... because i am using about a dozen extensions, it is going to be a bit tricky to remember which extension was installed from what method...

---

