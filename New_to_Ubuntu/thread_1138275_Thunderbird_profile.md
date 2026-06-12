---
title: "Thunderbird profile"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by expatCM on 2009-04-26
I keep my Thunderbird data on a separate drive to the operating system. I have just fresh installed Jaunty (ext4) and edited the profiles.ini to show the path to the mailboxes.  It worked ...  no issues.

Then I had this great idea to change the partition format of the data drive from ext3 to ext4 but to do so with a fresh format.  That was also easy.  I copied back the data files to the newly formatted volume and then had a problem.

Thunderbird will launch but it will not access the profile.  I have checked the path (which has not changed), the permissions of user / group.  I cannot see anything that is new or different.  Thunderbird wants to set up a new profile with mailboxes but since the existing profile works or at least should I wonder what the best approach to finding the real problem is?

I can read / write to the rest of the volume without any issue at all, it is only Thunderbird that is being challenging.

---

### Post by presence1960 on 2009-04-26
> **expatCM said:**
> I keep my Thunderbird data on a separate drive to the operating system. I have just fresh installed Jaunty (ext4) and edited the profiles.ini to show the path to the mailboxes.  It worked ...  no issues.

Then I had this great idea to change the partition format of the data drive from ext3 to ext4 but to do so with a fresh format.  That was also easy.  I copied back the data files to the newly formatted volume and then had a problem.

Thunderbird will launch but it will not access the profile.  I have checked the path (which has not changed), the permissions of user / group.  I cannot see anything that is new or different.  Thunderbird wants to set up a new profile with mailboxes but since the existing profile works or at least should I wonder what the best approach to finding the real problem is?

I can read / write to the rest of the volume without any issue at all, it is only Thunderbird that is being challenging.

In terminal run ```
thunderbird -profilemanager
``` When profilemanager comes up choose create a new profile. Follow prompts and choose profile folder you moved to /home/.mozilla-thunderbird. click finish when completed. You can now safely delete the Default profile which ran when you tried to start Thunderbird. **_NOTE: DO NOT DELETE the existing Thunderbird "Default" profile until AFTER you have created a new profile._**

Edit: you can add a profile folder in a different location thru profilemanager also, it doesn't have to be the default location. I believe this is how you had it set up. Follow the same instructions and then find your profile location to set it up. I just tried it and it works.

---

### Post by expatCM on 2009-04-26
Thanks for the help .....  I ran the profilemanager, set up a new profile and clicked to launch Thunderbird on completion.

Thunderbird opened but with the New Account Wizard rather than the mailboxes. (same as before)

I also had a look for the new profile and could not find it ......

---

### Post by presence1960 on 2009-04-26
> **expatCM said:**
> Thanks for the help .....  I ran the profilemanager, set up a new profile and clicked to launch Thunderbird on completion.

Thunderbird opened but with the New Account Wizard rather than the mailboxes. (same as before)

I also had a look for the new profile and could not find it ......

Did you delete the Default profile in profilemanager prior to running thunderbird again? Thunderbird will always use the default profile created until you create another and remove the default profile.

The default profile created when you install thunderbird is located at /home/.mozilla-thunderbird. The profile created by you will be located where you specify when creating a new profile in profilemanager.

If it is that fouled up maybe you can mark it for complete removal in Synaptic, then reinstall and try again.

---

### Post by expatCM on 2009-04-27
Something is clearly very strange .........

Yes, I deleted the default profile.   I have also used Synaptic to reinstall Thunderbird.  I have also changed the directory location of the data and changed the location of the mount point of this data drive.

Consistently the same thing happens.  Thunderbird opens and wants to run the new account setup.  For some reason it is not reading the path shown in the profiles.ini file ....  I have checked the path very carefully and it is correct (indeed it used to work) so I am struggling a bit here....

---

### Post by expatCM on 2009-04-27
I have solved this and I would like to share how ........

I looked at the program and the path in profiles.ini (reinstalling, editing, ...) but what I did not consider was the data.  I looked carefully and noticed that there was a very slight difference between the backup copy and what I had restored.  Slight here means only a few bytes.

What I then did was to delete the data and then copy the backup in again.  This time the copy size was exact and Thunderbird then ran without issue.

I do not know exactly which file caused this problem but I am really pleased that it is fixed ..........

---

### Post by presence1960 on 2009-04-28
> **expatCM said:**
> I have solved this and I would like to share how ........

I looked at the program and the path in profiles.ini (reinstalling, editing, ...) but what I did not consider was the data.  I looked carefully and noticed that there was a very slight difference between the backup copy and what I had restored.  Slight here means only a few bytes.

What I then did was to delete the data and then copy the backup in again.  This time the copy size was exact and Thunderbird then ran without issue.

I do not know exactly which file caused this problem but I am really pleased that it is fixed ..........

Thanks for sharing the solution, that is always good to know. At least your thunderbird is running right now :P

---

