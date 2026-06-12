---
title: "adding to startup applications"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by barbz127 on 2009-10-26
Hi all,

is there a special way to add startup applications? I have tried to add a job to kick off conky but....when i open up startup applications later it has removed my item.

but it allowed me to completely remove some items - is there a special trick to it?

Thanks
Paul

---

### Post by duanedesign on 2009-10-26
To have conky autostart on login create a small bash script called .conky_start.sh and save it to your /home.

```
gedit .conky_start.sh
```

copy the code below and past into the file. Save and close

```

#!/bin/bash
sleep 10 && conky;
```

This would start conky after 10 seconds after you login. The delay can be changed. Some sort of delay is desirable if you use compiz as well since conky works best if started after compiz. Make sure the script is executable:

```
chmod a+x .conky_start.sh
```

Now, add the script to your startup programs (menu: system->preferences->session->startup programs).Note, path to script is /home/<your user name>/.conky_start.sh

---

### Post by barbz127 on 2009-10-26
Thanks,
So far that is what I have done but when I add it into startup applications, next time I open it the entry for conky does not exist.

I am going to check my .config/autostart folder when I get back in front of the pc and see whats in there and I will just add it there.

Paul

---

### Post by ctc26 on 2009-10-26
Hi Paul,

I noticed you are using Karmic at the moment. There is a bug in the Startup Applications UI which causes new entries to be lost.

As a workaround:

Add the conky script to startup applications as you normally would. Then click the Add button once more, but instead of adding a new entry simply close the dialog box.

This will save the conky entry correctly. Get back to me if I havn't made myself clear enough.

ctc26.

---

### Post by barbz127 on 2009-10-26
Thanks ctc - I will give it a shot tonight :D

Cheers
Paul

---

### Post by barbz127 on 2009-10-27
worked thanks ctc :D

---

### Post by smozoma on 2010-02-09
I'm also using 9.10/Koala and am having trouble startup apps.

They don't get deleted like the person above was having trouble with -- they just don't work!

Is there some way to get them to work?  I'm trying to get "vino-preferences" (the remote desktop preferences window) to be loaded automatically, since for some reason Remote Desktop only works if the preferences window has been shown once after rebooting.

The session saver doesn't appear to work, either.

thanks

---

