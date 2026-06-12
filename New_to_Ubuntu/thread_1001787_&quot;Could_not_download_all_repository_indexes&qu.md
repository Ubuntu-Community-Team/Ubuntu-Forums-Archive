---
title: "&quot;Could not download all repository indexes&quot;..."
date: 2008-12-04
forum: New to Ubuntu
---

### Post by Mike Krall on 2008-12-04
After an official update download (6.06 LTS), if I click "check" the download hangs on 52 of 54, then I get attached screen shot. My internet connection is working, if that is what is being asked, but I cannot find 'repository address' in System > Preferences... would not know if the address was correct or not.

Would someone help me with this, please?

Mike

---

### Post by DJ_Peng on 2008-12-04
Never mind, I ran into something similar yet different yesterday.

---

### Post by drs305 on 2008-12-04
I checked the repository address and it still appears valid. The screenshot doesn't show the complete error message - the specific problem is offscreen right.  If this is an address you have successfully used in the past, the server may have been down for a time, in which case you should try again. If it still fails, you can either change servers or disable (temporarily) that specific repository.

It's been a while since I've used Dapper, but on later releases you get to the settings via Synaptic, Settings, Repositories. You can change servers or uncheck the backports option.

If you can't edit the Repositories via a gui-menu, you can edit your /etc/apt/sources.list and place a comment symbol # in front of the line containing the reference to dapper-backports. 

To edit sources.list:
```

gksudo gedit /etc/apt/sources.list

```

---

### Post by Mike Krall on 2008-12-05
Thanks for putting that up... I'm going to have to work at it and see if I can figure things out. Right now, I don't even know if I need more help or not. I'll get back to you either way but it will take me a while.

Mike

---

