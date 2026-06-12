---
title: "Setting User Privileges"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by DCS_Teacher on 2011-08-08
Hello all, I am completely new to Ubuntu so please forgive me if I ask any stupid questions.  Recently the school I work at had some laptops donated to it, but they did not have an operating system installed on them.  Since we have no budget for these computers I started looking into free OSs and have installed Ubuntu on a couple of the machines.  My question is this:

I would like to set up the machines so that they have 3 user accounts with varying levels of privileges and capabilities.

Admin Account: Able to do anything

Teacher Account: Not able to install new software, limited internet access (based off a list of blocked websites), Able to save files to specific folders

Student Account: Only able to access specified applications, extremely limited internet access (based off a list of allowed websites), Able to save files to a specific folder, resets settings on logout/login

I know I have seen computers with these types of restrictions, but am not really sure where to start, especially in an unfamiliar OS.

Thanks for any suggestions.

---

### Post by LowSky on 2011-08-08
hi welcome to the forums

to add users see this:
[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

to limit internet cabablilty look at dansgardian:
[https://help.ubuntu.com/community/DansGuardian](https://help.ubuntu.com/community/DansGuardian)


hope that helps you get started.

---

### Post by Gryllida on 2011-08-08
Ubuntu has Administrator users (the first one) and Desktop users (the second one). For more information, see here:

[https://help.ubuntu.com/11.04/ubuntu-help/user-accounts.html](https://help.ubuntu.com/11.04/ubuntu-help/user-accounts.html)

If you want to restrict a student account, you would need to create a desktop user account and restrict it manually. The "System -> Administration -> Users and Groups" allows some level of customisaion if you click the "Advanced settings" button.

----

Please respond as to whether this helps to solve the problem.

---

