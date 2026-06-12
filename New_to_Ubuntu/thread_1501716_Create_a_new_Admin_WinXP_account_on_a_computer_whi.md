---
title: "Create a new Admin WinXP account on a computer while using Ubuntu Live CD"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by hanzj on 2010-06-04
Hello,
We have a Windows XP (Home/Basic) computer. When powered it on, it asks for the username and password. We already have the username, but not the password. 

Is it possible to create a new WinXP admin account while using a Ubuntu Live CD in the WinXP computer?

Or, is it possible to find out the WinXP current password so that we can log on to the Win XP computer in the usual route?

---

### Post by aysiu on 2010-06-04
You can use the Ubuntu live CD to reset any Windows password.

Instructions here:
[http://www.psychocats.net/ubuntucat/resetwindowspassword/](http://www.psychocats.net/ubuntucat/resetwindowspassword/)

---

### Post by hanzj on 2010-06-04
Thanks so much. The WinXP computer doesn't have access to the internet yet, so I need to download all the necessary Ubuntu packages while away from the WinXP computer. Can you tell me all the debs I need to download to make the LiveCD-approach work? Thanks.

---

### Post by xpod on 2010-06-04
Depending on how the machine was initially setup sometimes you`ll have a hidden unsecured admin account accessible via safe mode from where you can make any necessary changes.
Failing that, the method mentioned above would be the obvious next step.

---

### Post by aysiu on 2010-06-04
> **hanzj said:**
> Thanks so much. The WinXP computer doesn't have access to the internet yet, so I need to download all the necessary Ubuntu packages while away from the WinXP computer. Can you tell me all the debs I need to download to make the LiveCD-approach work? Thanks.
This:
[http://packages.ubuntu.com/lucid/chntpw](http://packages.ubuntu.com/lucid/chntpw)

---

### Post by hanzj on 2010-06-04
thanks. hope that is the only one that's needed, coz i won't have net access on the comp. 8-)

---

### Post by new_tolinux on 2010-06-04
> **xpod said:**
> Depending on how the machine was initially setup sometimes you`ll have a hidden unsecured admin account accessible via safe mode from where you can make any necessary changes.
Failing that, the method mentioned above would be the obvious next step.
You don't have to go into safe-mode to try that.
If you're using the default welcome-screen (click on any username and then type the password), you can access the original login-screen by pressing CTRL+ALT+DEL twice.
Use "administrator" as username and don't type a password.

---

### Post by hanzj on 2010-06-04
new_tolinux,
1. when you say "default welcome-screen", do you mean the screen where the person's name is already put in, and all i have to do is enter the password (which is unknown)? 

2. when you say "pressing CTRL+ALT+DEL twice" do you mean doing the combo one after another? Or do I have to wait until something happens before doing the 2nd "ctrl-alt-del"?

---

### Post by xpod on 2010-06-04
> **new_tolinux said:**
> You don't have to go into safe-mode to try that.
If you're using the default welcome-screen (click on any username and then type the password), you can access the original login-screen by pressing CTRL+ALT+DEL twice.
Use "administrator" as username and don't type a password.

I believe getting the old Windows 2000 login you mention only works in XP Pro hence the reasoning behind the Safe Mode approach. It covers both Pro & Home.



 > **hanzj said:**
> new_tolinux,
1. when you say "default welcome-screen", do you mean the screen where the person's name is already put in, and all i have to do is enter the password (which is unknown)? 

2. when you say "pressing CTRL+ALT+DEL twice" do you mean doing the combo one after another? Or do I have to wait until something happens before doing the 2nd "ctrl-alt-del"?

Assuming it is indeed XP Pro just hitting CTRL-ALT-DEL twice in quick succession should bring it up.

---

### Post by hanzj on 2010-06-04
No, the computer is Windows XP Home (or is it called Basic?).

---

### Post by xpod on 2010-06-04
> **hanzj said:**
> No, the computer is Windows XP Home (or is it called Basic?).


I`m sure many here *would* call it "basic" but the [Safe Mode method ](http://oit.ncsu.edu/resnet/xp-passwords-admin)  will tell you if there is a hidden account regardless.

---

### Post by new_tolinux on 2010-06-04
> **hanzj said:**
> new_tolinux,
1. when you say "default welcome-screen", do you mean the screen where the person's name is already put in, and all i have to do is enter the password (which is unknown)? 

2. when you say "pressing CTRL+ALT+DEL twice" do you mean doing the combo one after another? Or do I have to wait until something happens before doing the 2nd "ctrl-alt-del"?
1. "default welcome screen" -> that list with users, you'll click on the desired account and you'll type the password. Not the old Windows NT/2000/95/98 screen where there's a username that you'll have to change manually to login as another user <edit> (that old screen is the one you should get after pressing CTRL+ALT+DEL twice and where you should put "administrator" as username) </edit>
2. I mean: press CTRL+ALT+DEL at the same time, release the three keys and directly after you've released them press CTRL+ALT+DEL at the same time again.
<edit>What I did most times I did need that prompt was pressing (and holding) CTRL and ALT, while pressing DELETE twice. ;)</edit>
> **xpod said:**
> I believe getting the old Windows 2000 login you mention only works in XP Pro hence the reasoning behind the Safe Mode approach. It covers both Pro & Home.

Assuming it is indeed XP Pro just hitting CTRL-ALT-DEL twice in quick succession should bring it up.
Assuming that it's indeed XP just hitting CTRL+ALT+DEL twice should bring it up. It really has nothing to do with XP home or XP pro, as it works on both and you'll don't need save-mode for it to work.
Only 1 little thing...... If you've installed service-packs, the chances are that the default account is disabled. Normally that doesn't happen if you installed XP with any service pack built in, only if you apply the service packs after installing.

---

### Post by Mark Phelps on 2010-06-05
You can Google for Trinity Rescue Kit, download and burn that, and then boot from it.  It will allow you to blank any and all MS Windows passwords.  After that, you can reboot into MS Windows and set the passwords to what you want.

---

