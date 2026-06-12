---
title: "GUI shutdown not working"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by wapitiscat on 2009-02-09
I have 8.1 on a Compaq nx9008 laptop and clicking the shutdown option in the dropdown menu results in a restart. Issuing the shutdown -h now command in terminal shuts the system down normally. This is my 6 year old's machine so I'd like to get the GUI option for shutdown to work. Any ideas?

---

### Post by NT4usB on 2009-02-09
You have wireless on that?
I've read there's a connection between wireless, alsa, and shutdown gui not working/rebooting.
Can you click the gui to shutdown then Ctrl+Alt+F1 to switch to the tty? Watch for hangs/errors during the shutdown process.

---

### Post by Vadi on 2009-02-09
I found that pressing ctrl+alt+backspace after the shutdown fails seems to work. I'm unable to reproduce this on a consistent basis though.

Since this is more of a bug, you should report here: [http://launchpad.net/ubuntu](http://launchpad.net/ubuntu)

---

