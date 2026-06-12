---
title: "exit all programs when installing?"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by PGScooter on 2009-05-11
Hi, I'm just wondering if it is usually recommended to exit all programs when installing something (via apt-get). If a certain program needs to be closed, will apt prompt for that?

I know that it would not hurt, but when I have a lot of open programs, it would be a pain to close everything and then reopen.

thank you

---

### Post by Didius Falco on 2009-05-11
As long as it is a new program, it shouldn't be a problem. If there should be a conflict, you can bet Synaptic/apt-get will squawk about it. <G>

Regards,

Didius

---

### Post by fourthofjuly on 2009-05-11
the modular nature of linux allows you to keep working on a program even if some other dependent program is being installed / updated...

i do not think apt will ever prompt you to close some program since it is not at all required...

i myself was surprised when on a running system i could restore my entire ubuntu installation from the commandline using a tarball backup file... everything including my home folder, configuration files, installed programs etc. were restored just as i had saved in the tarball... this on a live running system... unbelievable, but true

---

### Post by NightwishFan on 2009-05-11
Close all apt/synaptic related software. If any are open apt should inform you anyway. Generally if you update running software, it should be fine, though you may need to restart the application to get the effects of the update.

---

### Post by ashmew2 on 2009-05-11
The only programs you need to close when installing stuff are the other ones capable of installing stuff...That's a security measure...
If you wanted to know like if you were upgrading firefox from 3.0.1a to 3.0.1b and you were still using the 3.0.1a firefox that wouldnt be a problem. All the improvements which were added/removed , will be available once you restart that application.

---

### Post by PGScooter on 2009-05-11
great! thank you for all of the replies. It seems that for my purposes I'm pretty much safe.

I do think that it is important to save your data and be prepared for the case where you have to restart (your computer, or applications) when doing updates because I have had a few buggy things happen. But I have not had any such cases when installing new software.

---

### Post by Viva on 2009-05-11
Firefox gives you errors if you use it while updating it or xulrunner. Other than that, I've never experienced any problems.

---

### Post by PGScooter on 2009-05-11
> **Viva said:**
> Firefox gives you errors if you use it while updating it or xulrunner. Other than that, I've never experienced any problems.

Errors or warnings? Meaning, does it try to do the update and partial do it, and fail. Or does it try to do it and then say it can't because firefox is running?

I guess my question is: even in that case, it's still not that bad because you can just exit firefox and install it again and it will work, right? or is there more to it?

I'm just trying to think of the worst case scenario and how likely that would be.

---

### Post by Viva on 2009-05-12
> **PGScooter said:**
> Errors or warnings? Meaning, does it try to do the update and partial do it, and fail. Or does it try to do it and then say it can't because firefox is running?

I guess my question is: even in that case, it's still not that bad because you can just exit firefox and install it again and it will work, right? or is there more to it?

I'm just trying to think of the worst case scenario and how likely that would be.

Errors in the firefox window you're using.The update will be successful and everything will be fine after restarting firefox.

---

