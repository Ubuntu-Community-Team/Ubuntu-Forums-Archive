---
title: "nvidiactl permissions"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by Marquis Textures on 2009-05-15
So I was having graphics problems and now it's fixed "sorta".  But I have to type in a command on every reboot or every time I wake my computer from sleep mode to regain permissions for my card to do direct rendering.

When I type ```
glxinfo | grep rendering
```

I get ```
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose) 			 		 	 	  	
```

Then if I enter this command ```
sudo chmod a+rw /dev/nvidia*
```

I get direct rendering: YES!

So what steps should I be taking to fix these permissions I have absolutely no idea where to look or start so I don't have to type in the chmod 10 times a day.

---

### Post by izar on 2009-06-21
i found this command in some thread:
```
chmod 666 /dev/nvidia*
```

---

