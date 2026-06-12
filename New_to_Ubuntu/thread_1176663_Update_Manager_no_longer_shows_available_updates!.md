---
title: "Update Manager no longer shows available updates!"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by Mr, Bean on 2009-06-02
A few days ago i realise that update manager running on my ubuntu 9.04 machine stopped showing the available updates in the notification area. Im sure there is probably an easy way to fix this, but i cant find any info on this problem anywhere else!:confused:
 it is really frustrating having to open update manager just to check if it has any updates. 
(If anyone needs any more infomation just ask)

Any help is much appreaciated!
Thx (in advance):p

---

### Post by Tibuda on 2009-06-02
It will only show by default after a week, or if there's a security update.

---

### Post by steeleyuk on 2009-06-02
You can change this behaviour by doing ALT+F2 > type gconf-editor > /apps/update-notifier > uncheck auto_launch.

This reverts back to the old behaviour of Intrepid et al.

---

### Post by Tibuda on 2009-06-02
> **steeleyuk said:**
> You can change this behaviour by doing ALT+F2 > type gconf-editor > /apps/update-notifier > uncheck auto_launch.

This reverts back to the old behaviour of Intrepid et al.

Thanks, I didn't knew it.

---

### Post by Mr, Bean on 2009-06-03
> **steeleyuk said:**
> You can change this behaviour by doing ALT+F2 > type gconf-editor > /apps/update-notifier > uncheck auto_launch.

This reverts back to the old behaviour of Intrepid et al.
I tried this but there is no option for auto_launch.
there is just

autoclose_install_window
check_dist_upgrades
first_run
launch_time
remind_reload
show_details
show_versions
window_size

---

### Post by mcduck on 2009-06-03
> **Mr, Bean said:**
> I tried this but there is no option for auto_launch.
there is just

autoclose_install_window
check_dist_upgrades
first_run
launch_time
remind_reload
show_details
show_versions
window_size

You are now looking at options for update-manager, not update-notifier like steeleyuk suggested.. ;)

---

### Post by Mr, Bean on 2009-06-03
> **mcduck said:**
> You are now looking at options for update-manager, not update-notifier like steeleyuk suggested.. ;)
Oh ok i've unticked it now. It should be working now
thx everyone for your help

---

