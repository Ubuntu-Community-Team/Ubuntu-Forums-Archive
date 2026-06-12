---
title: "panel is missing!"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by rkakkar on 2009-03-10
my main panel went missing on reboot!! i have none of the panels in gnome and can't access anything!! how can i bring the panel back?

---

### Post by rkakkar on 2009-03-10
i installed some custom fonts in my $HOME/.fonts directory and changed my gnome display properties to use that font everywhere. when i rebooted the panel went missing!

---

### Post by rkakkar on 2009-03-10
any help?! my system is practically unusable! i need this fixed urgently!

---

### Post by Ms_Angel_D on 2009-03-10
try this while your logged in hit 

1)alt+f2 
2)Run nautilus
3)In your home directory if hidden files aren't shown hit ctrl+h
4)remove the folder .gconf/apps/panel
5)log out and back in

No promise it will work but it's worth a shot.

---

### Post by rkakkar on 2009-03-10
> **MetalHellsAngel said:**
> try this while your logged in hit 

1)alt+f2 
2)Run nautilus
3)In your home directory if hidden files aren't shown hit ctrl+h
4)remove the folder .gconf/apps/panel
5)log out and back in

No promise it will work but it's worth a shot.


didn't work!! :(

i deleted the entire .gconf directory. it restored my theme but the panel is still missing!

---

### Post by Ms_Angel_D on 2009-03-10
ok try this then (Please note I'm guessing here so I don't offer promises on these solutions)

1)ctrl-alt-f1
2)then try this command: sudo apt-get install gnome-panel
4)Then ctrl-alt-f7 to get back to the GUI.

---

### Post by ready4thebreak on 2009-03-10
Press Alt+ F2.
Run gconf-editor.
Press Apps drop-down arrow.
Press Panel drop-down arrow.
Select the general tab.
Look at the dialog area and right-click toplevel_id_list.
Select edit key.
Add top_panel
Add bottom_panel 

And then for safe measures log out and then log back in. I had this exact same problem when I first started Ubuntu back in August and here I am 6 months later giving my own directions. Hope all goes well! Don't give up just yet.

---

### Post by rkakkar on 2009-03-10
> **MetalHellsAngel said:**
> ok try this then (Please note I'm guessing here so I don't offer promises on these solutions)

1)ctrl-alt-f1
2)then try this command: sudo apt-get install gnome-panel
4)Then ctrl-alt-f7 to get back to the GUI.

this worked!! thank you all!! :)

---

### Post by rkakkar on 2009-03-10
how do i mark this thread as solved?

---

### Post by Ms_Angel_D on 2009-03-10
glad I was able to help :D Look under thread tools at the top you should have to option mark the thread as solved ;)

---

### Post by hatten on 2009-03-10
you cannot until they upgrade the forums

---

### Post by High Camp on 2009-03-11
Hi

Not to hijack the thread, I was, oddly enough, looking for a way to get rid of my Gnome-Panel in favor of XFCE. For anyone looking use these instructions:
Press Alt+ F2.
Run gconf-editor.
Press Apps drop-down arrow.
Press Panel drop-down arrow.
Select the general tab.
Look at the dialog area and right-click toplevel_id_list.
Select edit key.
Add a hash (#) at the begging of the key and then close.
I didn't have to log out but you may have to.

Thanks for the help,

---

