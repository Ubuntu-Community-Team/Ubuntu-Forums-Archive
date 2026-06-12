---
title: "Openshot Unmet Dependencies"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by brad1138 on 2011-05-06
I am having the exact same problem, I upgraded from 10.10 to 11.04 without any errors or problems, and am trying to install openshot.

I did find this fix (haven't tried it yet) [http://www.bbgamer.co.uk/archives/95](http://www.bbgamer.co.uk/archives/95) The poster of this fix was having the same prob and apparently this fixed it. 

Anyone see a reason not to try this fix?

Thank you,
Brad

*Mod Note:* This thread was spun off from [http://ubuntuforums.org/showthread.php?p=10780597#post10780597]("http://ubuntuforums.org/showthread.php?p=10780597#post10780597")

---

### Post by brad1138 on 2011-05-06
well that fix did not work. I tried installing python-mlt4 through SPM, it installed but I still can't install openshot, same problem.

---

### Post by brad1138 on 2011-05-06
I have been trying to install python-mlt3 through SPM again and I have been trying to install the dependencies it complains about.

First it complains about not being able to install libmlt3, so I installed libmlt3, which uninstalls libmlt++3 and libmlt4. Now I try to install python-mlt3 again and it complains about not having libmlt++3. 

I tried this a couple times back and forth. Apparently python-mlt3 want's libmlt3 and libmlt++3 installed at the same time, put SPM wont allow that. 

I got no clue where to go from here.

Brad

---

### Post by brad1138 on 2011-05-06
DayLite, do you happen to have Kdenlive installed? I do and I found another post by someone w/11.04 that installed it and then could not install openshot, just a thought. Hopefully someone will chime in here to let me know which one of my ideas are going in the right direction and which are crap :)

Brad

---

### Post by jtarin on 2011-05-06
> **brad1138 said:**
> I have been trying to install python-mlt3 through SPM again and I have been trying to install the dependencies it complains about.

First it complains about not being able to install libmlt3, so I installed libmlt3, which uninstalls libmlt++3 and libmlt4. Now I try to install python-mlt3 again and it complains about not having libmlt++3. 

I tried this a couple times back and forth. Apparently python-mlt3 want's libmlt3 and libmlt++3 installed at the same time, put SPM wont allow that. 

I got no clue where to go from here.

BradI found that if I install this Shotwell on my 10.10 it wants to remove a lot of my multi-media applications I don't want removed (VLC Player being one). If it was me wanting this type of application I would be looking for another to do the job.....this one spells trouble to me.

---

### Post by drs305 on 2011-05-06
This thread was spun off from [http://ubuntuforums.org/showthread.php?p=10780597#post10780597]("http://ubuntuforums.org/showthread.php?p=10780597#post10780597")

Even though the problem may appear identical, we ask users to begin a new thread for extended posts regarding your own situation.

---

### Post by jtarin on 2011-05-06
Redundant message deleted.

---

### Post by beew on 2011-05-06
I have a similar problem.
[URL="http://ubuntuforums.org/showthread.php?t=1750512"]http://ubuntuforums.org/showthread.php?t=1750512
[/URL]
I also posted the terminal output.

I have noticed for a while that OpenShot and Kdenlive seem to be having some compatibility problems, maybe over conflicting versions of melt.

---

### Post by brad1138 on 2011-05-07
> **beew said:**
> I have a similar problem.
[URL="http://ubuntuforums.org/showthread.php?t=1750512"]http://ubuntuforums.org/showthread.php?t=1750512
[/URL]
I also posted the terminal output.

I have noticed for a while that OpenShot and Kdenlive seem to be having some compatibility problems, maybe over conflicting versions of melt.

Ya, I just wanted to try it, I saw it recommended somewhere. Kdenlive works fairly well but has a few bugs (1 making it crash and disappear instantly) Maybe I will just stick with it though.

Thanks,
Brad

---

### Post by brad1138 on 2011-05-07
Well, I hadn't noticed, but trying to install openshot uninstalled kdenlive. When I reinstalled kdenlive, it installs libmlt++3 & 4.

I think that may be the main issue. How common is it to have 2 conflicting programs like that?

---

