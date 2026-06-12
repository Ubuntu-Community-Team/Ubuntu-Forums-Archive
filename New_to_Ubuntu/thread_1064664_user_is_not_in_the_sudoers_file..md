---
title: "user is not in the sudoers file."
date: 2009-02-09
forum: New to Ubuntu
---

### Post by eabhvee on 2009-02-09
Hello,

I am trying to setup subversion as per this guide [https://help.ubuntu.com/community/Subversion](https://help.ubuntu.com/community/Subversion)

I created a new user group called subversion and added myself and root to it. After that I used gconf-editor to enable 'show all users' option. Now I can not access System --> Administration --> Users and Groups. I get an error message 
'Could not authenticate. An unexpected error occured'

I try to run Synaptic from menu, I get the following message
'Failed to run /usr/sbin/synaptic as user root.'

I try to run synaptic from terminal, I get the following message.
'user is not in the sudoers file'.

Can somebody help me to fix this pleaase.

Cheers,
Abhi

---

### Post by yeats on 2009-02-09
I'm looking at the page you link to:
>    
   1.Choose System > Administration > Users and Groups from your Ubuntu menu.
   2. Select the Group tab
   3. Click the 'Add Group' button
   4. Name the group 'subversion'
   5. Add yourself and www-data (the Apache user) as users to this group
          
*(Note: in order to see www-data you may need to modify root's /apps/gnome-system-tools/users/showall GConf setting; see GConfEditor) 

   6. Select 'OK' to commit your changes and exit the app. 

You have to logout and login again before you are a member of the subversion group, and can do check ins. 

Did you follow each step exactly as written, then did you log out and log back in?

---

### Post by eabhvee on 2009-02-09
Hi,

Thanks for the quick reply.

I followed all the steps except one.

I should have enabled the show all users option first before adding the users to subversion group. But I failed to do that and I added root to the group which was not mentioned in the procedure.
After this I am not able to access user-admin. I have fixed the synaptic problem after booting in to rescue mode and adding myself in to the sudoers file. But I still have problem using user-admin.

Regards,
Abhi

---

