---
title: "Chromium Close/Minimize/Maximize Buttons on WRONG Side (LEFT)"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by tcpkid_82 on 2010-07-08
I am using ubuntu 10.04 LTS and after installing chromium from Ubuntu Software Center i can see that the Close/Minimize/Maximize buttons are on the left side of the window (i am not using system icons, dont want to)... i want them to be on the right side because they push the tabs forward....

Any fixes? See screenshot for issue..

[IMG]http://i.imagehost.org/0105/Screenshot_3.png[/IMG]

[IMG]http://i.imagehost.org/0760/Screenshot-1.png[/IMG]

---

### Post by jtarin on 2010-07-08
Run Application Dialog (Alt+F2) or open a terminal and execute this command:

```
gconftool-2 --set /apps/metacity/general/button_layout --type string menu:minimize,maximize,close
```

---

### Post by tcpkid_82 on 2010-07-08
> **jtarin said:**
> Run Application Dialog (Alt+F2) or open a terminal and execute this command:

```
gconftool-2 --set /apps/metacity/general/button_layout --type string menu:minimize,maximize,close
```

Thanks! Works great even though it does that for all applications... Faster than configuring a theme!

---

### Post by anewguy on 2010-07-08
And a short note:

in 10.04, the buttons were changed to default to the left side instead of the right.

---

### Post by k3lt01 on 2010-07-08
> **anewguy said:**
> And a short note:

in 10.04, the buttons were changed to default to the left side instead of the right.My Chromium has them on the right while everything else has them on the left. It doesn't worry me but I'm now wondering if it is a bug.

---

### Post by anewguy on 2010-07-09
Don't know about Chromium - guess I should have said Ubuntu and it's apps default to the left beginning with 10.04.

---

### Post by themusicalduck on 2010-07-09
That's weird. It's on the right for me with the version from the Software Centre, but the version from the dev ppa has them on the left.

Maybe the 64bit version is a later version than the 32bit.

---

### Post by tcpkid_82 on 2010-07-09
> **k3lt01 said:**
> My Chromium has them on the right while everything else has them on the left. It doesn't worry me but I'm now wondering if it is a bug.

run this (in root terminal) to update your chromium software, then your buttons will be on the left. (i prefer them on the right)...

```
sudo apt-get update; sudo apt-get upgrade
```

---

### Post by k3lt01 on 2010-07-09
> **tcpkid_82 said:**
> run this (in root terminal) to update your chromium software, then your buttons will be on the left. (i prefer them on the right)...

```
sudo apt-get update; sudo apt-get upgrade
```Thanks, it's ok,it doesn't bother me.

---

### Post by jtarin on 2010-07-10
I have read that Chromium changed them to conform to the new convention of buttons on the left according to the wisdom of Lucid.You can control your user space more readily with Ubuntu Tweak. [Ubuntu Tweak make things easy.]("http://ubuntu-tweak.com/")

---

### Post by KdotJ on 2010-07-10
I ended up using the system window borders, and downloaded the lucid theme for chromium and the scroll bars. Now it fits in very well with everything else

---

