---
title: "problem with gtk-recordmydesktop"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by gauravgupta on 2010-11-09
i have installed recordmydesktop but it is capturing video which is not clear and smooth.
and have problem with gtk-recordmydesktop installation it says 

configure: error: You need pygtk >=2.4 and the appropriate development headers to proceed
please help ...

---

### Post by rampageoberon on 2010-11-09
Try installing from repository - you shouldn't need the header files in this case. Hope this helps.

```
sudo aptitude reinstall gtk-recordmydesktop
```

---

### Post by Hippytaff on 2010-11-09
After the install it might be worth doing
```

sudo apt-get update && sudo apt-get upgrade

```
just in case anything needs it :-)

---

### Post by toekneewood on 2010-11-09
You might want to also try
Istanbul is a desktop session recorder for the Free Desktop. It records your session into an Ogg Theora video file. To start the recording, you click on its icon in the notification area. To stop you click its icon again. It can make a screencast of the full screen or just of an area of the screen. It is even capable of recording audio from the default input channel.
```

sudo apt-get install istanbul

```

---

