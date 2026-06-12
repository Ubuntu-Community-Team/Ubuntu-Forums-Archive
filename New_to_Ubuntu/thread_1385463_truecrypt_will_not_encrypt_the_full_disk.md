---
title: "truecrypt will not encrypt the full disk"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by DestructionsRightHand on 2010-01-19
i have the first picture, attached is what it should offer.  I installed it using these steeps per [http://ubuntuforums.org/showthread.php?p=8493602](http://ubuntuforums.org/showthread.php?p=8493602)
**Step 1**
Go to the [TrueCrypt download page]("http://www.truecrypt.org/downloads") and scroll down until you get to the part where you select your Linux distribution and hardware platform.

**Step 2**
From the dropdown menu, select *Ubuntu - x86 .deb* (unless you're absolutely sure you install 64-bit Ubuntu, in which case you should get the x64 one).

**Step 3**
Click *Download*

**Step 4**
Right-click on *truecrypt-6.3a-ubuntu-x86.tar.gz* and select *Extract here*

**Step 5**
Double-click *truecrypt-6.3a-setup-ubuntu-x86*

**Step 6**
Select *Run*

**Step 7**
Select *Install TrueCrypt* and accept the license agreement

**Step 8**
This should launch GDebi (also called *Package Installer*). Click *Install Package*

Now if you go to Applications > Other > TrueCrypt, it should be in the menu.

---

### Post by shadow120 on 2010-01-19
the linux version doesnt let you encrypt the whole system drive because it dosent have the preboot authentication.  i have a thread about this in the security forum and someone said LUKS will do this but i havent tried it yet.

---

### Post by DestructionsRightHand on 2010-01-21
thanks thats what i was thinking

---

