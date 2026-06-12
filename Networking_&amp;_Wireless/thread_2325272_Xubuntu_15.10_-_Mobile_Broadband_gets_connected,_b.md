---
title: "Xubuntu 15.10 - Mobile Broadband gets connected, but no Internet Access"
date: 2016-05-20
forum: Networking &amp; Wireless
---

### Post by prahladyeri on 2016-05-20
Folks,


There is this [nagging bug #1508718]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/1508718") in 15.10 where some mobile broadbands of Huawei have a connection error. Basically, the *mobile broadband* connects but Internet doesn't work. Also, the connection is not editable from *Menu->Edit Connections->Mobile Broadband* and I face this error dialog when I click the edit button:

> > settings/nm-settings-connection.c.995 - Connection didn't have requested setting 'ppp'

Its all mentioned in the bug report and its given a confirmed status and high importance, but its not yet resolved. Can some of you please provide a fix for this bug or alternatively provide me a workaround? Plz help.

---

### Post by mörgæs on 2016-05-21
How does it work for 16.04?

The bug is not 'critical'. You will probably get more answers with a more precise thread title, for example 'Huawei modem'.

---

### Post by prahladyeri on 2016-05-21
Thanks a lot for your reply. I haven't tested this in 16.04 and I don't  want to since its just recently released. I'd prefer to get this fixed  in 15.10 itself since everything else in 15.10 is quite stable.

> The bug is not 'critical'.
Its kinda critical for me since my mobile broadband doesn't work with this bug unless I experiment like restart the *network-manager* a fifty times or unplug and replug the dongle several times.

> You will probably get more answers with a more precise thread title, for example 'Huawei modem'.
I understand, but I cannot change the title of this thread. Should I start another thread with a different title?

---

### Post by vasa1 on 2016-05-21
> **prahladyeri said:**
> ...
> You will probably get more answers with a more precise thread title, for example 'Huawei modem'.
I understand, but I cannot change the title of this thread. Should I start another thread with a different title?You can :)

[LIST]
[*]Click edit for the first post in this thread
[*]Click "Go Advanced" below the post and to the right hand side (between *Save* and *Delete*).
[*]Then look above your post for the title. Click in the adjacent text area and change what you need.
[/LIST]

Of course, this will only affect the title of the first post but that's what people see :)

If you still have trouble, just indicate what you'd like the title to be and one of us will fix it for you.

---

### Post by mörgæs on 2016-05-21
The bug report to which you linked has only posts for 15.10. Though not hard evidence it still gives weight to the thought that it could be fixed in 16.04.

Moreover, it's unlikely that anyone will fix this non-critical bug in 15.10 which has only two months of support left ('support' meaning that bugs related to security are fixed, not bugs in general).

---

### Post by prahladyeri on 2016-05-21
Something related to Mobile Broadband connections of *Huawei* dongles seems to have badly broken in 15.10. What happens is that I create a Mobile Broadband connection and it connects, but Firefox doesn't open any websites. Also, when I do something like **ping 8.8.8.8**, I don't get any response. I'm not alone in facing this issue, but there are a few others as seen in these forum links, but still there is no fix:

[https://answers.launchpad.net/ubuntu/+question/276327](https://answers.launchpad.net/ubuntu/+question/276327)
[Mobile Broadband connected but no internet access]("http://ubuntuforums.org/showthread.php?t=2299897")

Presently, the only workaround seems to be to unplug and replug the dongle in different USB slots. Or, as @srikumar found a workaround in the first link, to click *Auto Ethernet* instead of *Enable Mobile Broadband* on the Network menu. But how to get the *Auto Ethernet* menu when the dongle is inserted in the first place is still a mystery, so this workaround isn't really a workaround.

Can some of you provide a fix or workaround for this?

---

### Post by coffeecat on 2016-05-21
Threads merged. Please do not start duplicate threads for the same issue.

---

### Post by prahladyeri on 2016-05-23
@coffeecat, thanks for merging the thread. Let me also reference [this other post]("http://ubuntuforums.org/showthread.php?t=2325543") I had later created as it has some more information about the issue.

Can you provide some pointers as to where should I start to investigate this in order to get a fix?

---

### Post by prahladyeri on 2016-05-26
@coffeecat, et al. Can you suggest me any fix for this issue?

---

### Post by mörgæs on 2016-05-27
I don't know if I am part of 'et al.' 
If I am then I will just let you know that I am signing out of the thread. My point of view can be seen in post five.

Good luck.

---

### Post by prahladyeri on 2016-05-29
> I don't know if I am part of 'et al.'

Yup, I was referring to everyone in this thread!
Thanks  a ton! In case you can read this message, I can confirm that this is  resolved in 16.04 lts. Indeed, it was my bad to try and experiment with a  non-LTS version in the first place!

---

### Post by mörgæs on 2016-05-29
Good, please mark the thread 'solved' and spread the word: Always begin with the latest release when troubleshooting.

---

