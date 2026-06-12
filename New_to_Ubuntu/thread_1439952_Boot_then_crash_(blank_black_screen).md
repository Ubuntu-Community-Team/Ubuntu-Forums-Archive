---
title: "Boot then crash (blank black screen)"
date: 2010-03-26
forum: New to Ubuntu
---

### Post by den160593 on 2010-03-26
Hi,

On Karmic I've been working fine last couple of months using a newer kernel (2.6.32 i think it is) with the xorg-edgers open source ATI graphics cards as that was the only way for me to get compiz to work.

Worked fine earlier today. I installed any updates like normal. Now, whenever I try and boot into Ubuntu it starts to load, and then I get a blank black screen. I can still see the icon whilst loading, but then there's failure. Not sure why this has happen, perhaps due to some recent update?

Could anyone help me out

Thanks!!

---

### Post by den160593 on 2010-03-27
Can anybody help me out? Any idea why this might have happened?

---

### Post by den160593 on 2010-03-28
Anybody able to help?

---

### Post by achase79 on 2010-03-28
I had a problem like this, but I had the proprietory drivers from  ATI so I just reinstalled and it worked on my next reboot.

---

### Post by den160593 on 2010-03-28
Thanks for reply. Thing is, took ages to get my ATI card to work with compiz (proprietory drivers just didn't work for me...) so I'd prefer to see if this could be done without a re-install. Thanks though!

---

### Post by anewguy on 2010-03-29
> **den160593 said:**
> Hi,

On Karmic I've been working fine last couple of months using a newer kernel (2.6.32 i think it is) with the xorg-edgers open source ATI graphics cards as that was the only way for me to get compiz to work.

Worked fine earlier today. I installed any updates like normal. Now, whenever I try and boot into Ubuntu it starts to load, and then I get a blank black screen. I can still see the icon whilst loading, but then there's failure. Not sure why this has happen, perhaps due to some recent update?

Could anyone help me out

Thanks!!

This would appear to be a video driver problem - the way to check is when the blank screen appears hold down CTRL and ALT and press F1 -> if this opens a terminal window then it's your video driver.

Perhaps after one of the recent updates (a kernel update by chance?) the video driver was lost.  I would re-install the video driver if it was me.

Dave ;)

---

