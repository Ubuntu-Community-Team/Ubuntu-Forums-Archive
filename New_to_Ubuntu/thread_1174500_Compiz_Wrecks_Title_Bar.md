---
title: "Compiz Wrecks Title Bar"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by punong_bisyonaryo on 2009-05-31
I'm running Ubuntu Intrepid Ibex with an Nvidia card. Whenever I turn on Compiz, it wrekcs the title bar sometimes when my mouse is over it. It used to work fine two or three distros ago. And I'm not really sure what this phenomenon is called.

Anyone have an idea so I can file the appropriate bug report?

---

### Post by CatKiller on 2009-05-31
It's Emerald that decorates the windows with Compiz. You could try changing your Emerald theme to see if it helps.

---

### Post by steeleyuk on 2009-05-31
Emerald is optional, and not installed by default.

I think this is an issue with either the nvidia driver and/or the Human theme. Its a bug in one and its been around for a while. Not sure if its been fixed, I haven't looked recently.

You can try changing themes, some themes do this while others work fine. Or the alternative is to use Emerald...

---

### Post by anchorschmidt on 2009-05-31
Install the compiz config icon via add remove programs. Then right click on the icon and then try changing the window decorator. This might help.

---

### Post by punong_bisyonaryo on 2009-05-31
Thank you all for your replies. I'll try this out tonight to see if it works.

---

### Post by prvteprts on 2009-05-31
I agree with anchorschmidt.

Install ccsm and emerald, then under window decoration, change the value in the "command" text box from usr/bin/compiz-decorator to usr/bin/emerald.

---

### Post by punong_bisyonaryo on 2009-06-02
Yup! Emerald fixed it. Thanks everyone. So I guess this is a problem with the Human compiz theme then?

---

### Post by steeleyuk on 2009-06-02
Its possible. Though, I only seem to find people who have this problem with nvidia cards and the nvidia proprietary driver.

---

