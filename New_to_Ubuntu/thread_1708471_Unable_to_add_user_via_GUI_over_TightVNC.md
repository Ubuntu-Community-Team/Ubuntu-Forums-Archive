---
title: "Unable to add user via GUI over TightVNC"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by eu0 on 2011-03-16
I'm running headless Maverick Meerkat box with TightVNC 1.3.9-6.1 and all updates installed, and I connect by tunneling port 5901 (for display :1) over ssh.  I'm trying to write instructions so that a non-technical admin who connects similarly can add a user.  Everything works fine adding a user from the command line; however, in the GUI (System->Administration->Users and Groups) a click on the Add button only changes the button to orange for the duration that it has focus.  There is no other visible effect, not even an error dialog.  I see similar symptoms clicking the Advanced Settings button, but not for, say, the Manage Groups button.  Any ideas why this might be?

In case it helps, back when I had direct physical access and a monitor connected, the dialog behaved as expected.

---

### Post by seawolf167 on 2011-03-17
If you do the standard Unlock -> Add User -> Edit/Modify, are you able to make your changes regardless of the GUI color changes? I know that for me using UltraVNC sometimes the screen/focused window isn't polled accurately or fast enough, especially over a WAN connection, but the mouse clicks still work.

As a side note, any reason you aren't using SSH to access the box and write some simple scripts or aliases for them to use?

---

### Post by eu0 on 2011-03-17
Forgive my unfamiliarity with the Ubuntu GUI.  When I select System->Administration->Users and Groups, I get a password prompt and then a dialog that resembles this one from a Google image search: [http://www.liberiangeek.net/wp-content/uploads/2010/10/printer_users_mav_1_thumb1.png](http://www.liberiangeek.net/wp-content/uploads/2010/10/printer_users_mav_1_thumb1.png).  I don't know if that corresponds to the Unlock -> Add User -> Edit/Modify steps that you gave or not.

I am fairly certain that the issue isn't in the repainting; the VNC connection is quite responsive, and even after clicking Add User I see mouse-over animations for the buttons on the User Settings dialog.  In contrast, when I click Manage Groups (which works), the User Settings dialog loses focus and its buttons' mouse-over animations do not play.

Scripts are certainly an option.  It's just that the other admin will already be using VNC for other things, and also that it struck me as odd that the dialog would cease to function.  We'll be fine either way; I just wanted to know if I could make their life easier and whether I should file a bug.

---

