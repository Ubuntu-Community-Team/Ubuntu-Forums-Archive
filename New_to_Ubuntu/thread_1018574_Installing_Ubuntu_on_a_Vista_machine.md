---
title: "Installing Ubuntu on a Vista machine"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by sanubie on 2008-12-22
I'm just wondering, as everyone seems to be telling me I'll have issues installing Windows on a machine with Ubuntu already on it, about installing Ubuntu on a computer with Vista. 

Is it about the same as installing it over XP? Or does Vista make it more difficult?

---

### Post by Paddy Landau on 2008-12-22
I have a Windows Vista machine.

I got totally fed up with Windows and its nonsense, so I installed [Wubi]("http://wubi-installer.org/") (Windows Ubuntu Installer - the easy way to experiment with Ubuntu). It worked perfectly.

I uninstalled Wubi and installed Ubuntu in its own partition. It still worked perfectly.

Depending on your hardware, you may have some compatibility problems (e.g. my son's machine's wireless is designed to work **only** with Windows - doh!).

Use Wubi first to find out about compatibility problems, and if it works all OK, uninstall Wubi and install Ubuntu.

---

### Post by arochester on 2008-12-22
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by Duck2006 on 2008-12-22
Use the partition tool from with in vista to make the space for ubuntu then install ubuntu.

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by Paddy Landau on 2008-12-22
> **Duck2006 said:**
> Use the partition tool from with in vista to make the space for ubuntu then install ubuntu.
Why not let the Ubuntu LiveCD do the partition adjustments? It works well and is far easier than using Vista's partition program.

---

### Post by Duck2006 on 2008-12-22
> **Paddy Landau said:**
> Why not let the Ubuntu LiveCD do the partition adjustments? It works well and is far easier than using Vista's partition program.

Because vista is not the same as partition a xp or 2000 or me ect system, vista likes it own partition tool to partition the drives, it got some thing to do with the check sum that vista writes to it's logs to keep track of the drive sizes and so forth.

---

### Post by Paddy Landau on 2008-12-22
> **Duck2006 said:**
> Because vista is not the same as partition a xp or 2000 or me ect system, vista likes it own partition tool to partition the drives, it got some thing to do with the check sum that vista writes to it's logs to keep track of the drive sizes and so forth.
Thanks.

So that means that if LiveCD adjusts the partitions for Vista, then the Vista drive may be compromised?

---

### Post by Duck2006 on 2008-12-22
> **Paddy Landau said:**
> Thanks.

So that means that if LiveCD adjusts the partitions for Vista, then the Vista drive may be compromised?

Yes.

[http://www.ecoustics.com/pcw/reviews/132079](http://www.ecoustics.com/pcw/reviews/132079)

---

### Post by shabs on 2008-12-22
Agree with Duck on this one. Also the partition editor on vista is quite easy to use. I tried partition magic on vista once before and I ended up with weird sectors. 

@Paddy. Whats the need to install Wubi? If you need to check for compatibility wouldn't the LiveCD do the trick?

---

### Post by Captain_tux on 2008-12-22
> **Paddy Landau said:**
> Thanks.

So that means that if LiveCD adjusts the partitions for Vista, then the Vista drive may be compromised?

Possibly... but not definitely. I've done it once using Vista's partitioning tool and twice without - to this date, I haven't had problems.

---

### Post by sanubie on 2008-12-22
Thanks a lot everyone! I guess maybe I should just go ahead and buy a machine with Vista. Staples has some pretty cheap. Then I'll just install Ubuntu. 

About the Vista partition program, can anybody provide more information? I partition the drive first in Vista? That's somewhat confusing... then how do I install Ubuntu on the partition created inside Vista? When I insert the Ubuntu disk won't it ask to partition it again? Or will it just let me select the partition created in Vista?

---

### Post by Duck2006 on 2008-12-22
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by Paddy Landau on 2008-12-22
> **shabs said:**
> @Paddy. Whats the need to install Wubi? If you need to check for compatibility wouldn't the LiveCD do the trick?
Yeah, good point. That's the old Windows in me coming out... I forget that on Linux you don't have to install anything to use it!

---

