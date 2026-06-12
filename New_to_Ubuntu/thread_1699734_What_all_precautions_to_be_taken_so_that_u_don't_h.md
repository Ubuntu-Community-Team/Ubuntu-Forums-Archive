---
title: "What all precautions to be taken so that u don't have dependency problems?"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by krishna.988 on 2011-03-04
What all precautions to be taken so that u don't have dependency problems, while upgrading ubuntu..repositories, source list etc..? Please suggest.. Because I always have some or the other issues while upgrading to a newer version of Ubuntu..

---

### Post by mcduck on 2011-03-04
As long as you use software from Ubuntu's own repositories, you shouldn't have any problems.

If you are using any third-party repositories you should disable them before upgrading. (of course depending on what kind of stuff you have installed from such repositories you might still get some problems).

Also make sure you have the *ubuntu-desktop* installed when doing upgrade. That makes sure you get all the new packages that might not exist on your current release version.

Any manually installed stuff, from source or by other means, you will have to handle manually after the upgrade. As such programs weren't installed through the package management, the package manager of course can't handle updating them either.

---

### Post by krishna.988 on 2011-03-04
> **mcduck said:**
> As long as you use software from Ubuntu's own repositories, you shouldn't have any problems.

If you are using any third-party repositories you should disable them before upgrading. (of course depending on what kind of stuff you have installed from such repositories you might still get some problems).

Also make sure you have the *ubuntu-desktop* installed when doing upgrade. That makes sure you get all the new packages that might not exist on your current release version.

Any manually installed stuff, from source or by other means, you will have to handle manually after the upgrade. As such programs weren't installed through the package management, the package manager of course can't handle updating them either.

Thanks!! I upgraded from 10.04 LTS to 10.10 this morning. After upgrading it  showed me some notification applet is not working with delete and don't  delete option and later. I chose delete. 
When I tried to install startup-manager from ubuntu software center. It  showed to enable universe source and started installing with updating  cache it kept on asking for 10.10 CD as I had installed by directly  mounting the cd  ISO..I could'nt insert the cd.I tried mounting again  but it kept on prompting for CD. then I canceled updating cache, then  startup manager installed successfully msg was shown..
Then I tried to update ubuntu, using update manager partial upgrade  message is shown, saying not all updates were installed..Not sure what  to do..Please help!!

---

