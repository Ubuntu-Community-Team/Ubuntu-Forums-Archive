---
title: "Application to tell about status of internet connection in ubuntu Jaunty"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by t_k_majumdar on 2009-05-13
Hi -

While trying to solve the problem for internet connectivity, I came across an interesting article at: [http://ubuntuforums.org/showthread.php?t=731251](http://ubuntuforums.org/showthread.php?t=731251) wherein LaRoza spoke of a small programme in bash that "pops up a dialogue if an internet connection is not detected". "It pings google, and if it fails, it will give a popup notifying you, if it suceeds, it waits 30 seconds and does it again".

Such a programme would be very useful for me at least. Can anyone guide me for finding such one for running in ubuntu linux 9.04?

Thanks in advance.

---

### Post by orethrius on 2009-05-13
The program is listed in the [final post](http://ubuntuforums.org/showpost.php?p=4562326&postcount=6) on that page.  Open Main Menu > Accessories > Text Editor, select the code in the browser window and copy it (Ctrl-C), switch to the Text Editor and paste it (Ctrl-V).  Save the file as ~/connstat.sh (or whatever other clever name you think up; even the .sh isn't strictly necessary, but the ~/ makes sure that it saves in your home directory).  Find the file you saved, right-click it, select Properties > Permissions tab, then check "Allow executing file as program" and close that window.  Now, when you double-click the file, you will have the option to Run it or Display Contents (something to that effect).

UPDATE: The original code uses core system utilities that are still available in 9.04.  No update to the code is needed at this time. :)

EDIT: Personally (if you're using Ubuntu or some blend of Kubuntu or Xubuntu that has a Gnome desktop, this should work for you as well), I rely on the Network Monitor panel applet for connection status purposes.  You can get it simply by right-clicking the panel, selecting "Add to Panel...", then selecting "Network Monitor" and clicking "Add".  That's all there is to it! :)

---

### Post by t_k_majumdar on 2009-05-19
Many thanks orethrius for your reply. I tried to run the code in terminal after saving it in a file but the output is somewhat not what I expected and therefore not useful. 	

Your last suggestion for using "Network Monitor panel applet" for connection status purposes was more useful. I am satisfied with it. However, its installation was not that easy in Ubuntu 9.04 aka Jaunty Jackalope. I used the following steps for it:

1. The applet was not in the "Add to panel" list originally. So, I install it by "sudo apt-get install gnome-netstatus-applet" command in a terminal.

2. The applet was still not in the "Add to panel" list.Hence, I had to issue "killall gnome-panel" in terminal. These 2 steps were as per FuturePilot's reply to post [http://ubuntuforums.org/showthread.php?t=1132024](http://ubuntuforums.org/showthread.php?t=1132024).

3. Now I could follow the rest of your suggestion easily.

---

### Post by appier on 2009-10-14
> **t_k_majumdar said:**
> sudo apt-get install gnome-netstatus-applet

Good advice: thank you!

---

