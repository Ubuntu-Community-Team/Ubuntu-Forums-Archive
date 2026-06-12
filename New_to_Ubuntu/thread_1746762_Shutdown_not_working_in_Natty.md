---
title: "Shutdown not working in Natty"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by harfin on 2011-05-02
Upgraded to 11.04 a couple of days ago, and am now unable to electronically shut down my PC (Dell Dimension E5520) using any one of the normal system shut down options.

My only option at the moment is to physically switch off the PC.

Most of the applications seem to work fine and I love the look of the new screen(s). 

Can anyone help please?

**_Update at 11:30 BST_**
After a bit further digging, I noticed there were some processes running (via System Monitor) preface 'zeitgist'; I highlighted the three processes, and clicked 'stop process' and voila I was able for once to shut down the PC via the usual option to shut down via the drop down menu item of the 'light-switch' (toolbar) icon.  

Any help in identifying what the problem is?

Alan

---

### Post by spikoley on 2011-05-02
Try shutting down via the shell and see if it brings up any errors.

```
sudo halt
```

or

```
sudo reboot
```

---

### Post by harfin on 2011-05-02
Shutdown works fine now from the toolbar icon.
Forcing the 'end process' seems to have done something!
Oh and by the way, the shutdown and restart commands from the shell also work (without error).

Hmmm.

Thanks for the help

Alan

---

### Post by MikeG0 on 2011-05-05
Same here.  Just got a new Dell Latitude 5520 *laptop* installed 11.04.  Everything looked swell, but the shut down hung.  Also, hibernation didn't work.  Dug around the bug reports and found some stuff about acpi.  ([http://www.brighthub.com/computing/linux/articles/39504.aspx](http://www.brighthub.com/computing/linux/articles/39504.aspx)) 

I disabled acpi and the shutdown worked, but still no hibernation.

Found a post that recommended  downloading the 10.10 dvd iso from support.dell.com.

Dell's 10.10 iso works.

Gonna wait for 11.04 to stabilize a little bit longer.

---

