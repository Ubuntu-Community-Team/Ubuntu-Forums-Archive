---
title: "Evolution to Thunderbird"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by Captain Legless on 2009-02-07
Does anyone have a simple method of moving mail/calender/contacts from Evolution to Thunderbird please?

---

### Post by Gramps on 2009-02-07
Thunderbird doesn't have a calendar as far as I know. Try Tools/Import to import the mail and address book(contacts)

---

### Post by Captain Legless on 2009-02-07
> **Gramps said:**
> Thunderbird doesn't have a calendar as far as I know. Try Tools/Import to import the mail and address book(contacts)

I have a calendar in my installation :)

As for using 'import', yes I know the idea begind it but I need to know what files I have to import and where I find them. e.g. pst files as found in Outlook , or CSV files...etc.:confused:

---

### Post by howefield on 2009-02-07
Contacts can be moved by exporting address book as a vcard then convert it here to a format thunderbird can take.

[http://labs.brotherli.ch/vcfconvert/](http://labs.brotherli.ch/vcfconvert/)

This article seems to cover it...

[http://johnpalermo.ca/?p=20](http://johnpalermo.ca/?p=20)

---

### Post by Gramps on 2009-02-08
> **Captain Legless said:**
> I have a calendar in my installation :)


:-k Sorry my version doesn't have a calendar....

---

### Post by Captain Legless on 2009-02-08
> **Gramps said:**
> :-k Sorry my version doesn't have a calendar....

Hey don't be sorry, you attempted to help me out! I installed  "lightening" which is a multi purpose calender that integrates into Thunderbird perfectly. It can be found in the Synaptic Manager 8-)

---

### Post by Captain Legless on 2009-02-08
Well I've managed to import the calender succesfully and the contacts to a fashion BUT I've no idea how to import the emails.

If it's of any help I do have both Outlook and Thunderbird installed on my XP partition. Could I maybe import things from there?

---

### Post by ugm6hr on 2009-02-08
> **Captain Legless said:**
> If it's of any help I do have both Outlook and Thunderbird installed on my XP partition. Could I maybe import things from there?

Do you access the emails from Windows T-bird?

If yes - just copy the profile (find location in T-bird prefs)) to the profile location in Ubuntu.

Since you use all these email readers, do you use IMAP email?  If yes - just create settings again in T-bird.

---

### Post by Captain Legless on 2009-02-08
> **ugm6hr said:**
> Do you access the emails from Windows T-bird?

If yes - just copy the profile (find location in T-bird prefs)) to the profile location in Ubuntu.

Since you use all these email readers, do you use IMAP email?  If yes - just create settings again in T-bird.

OK - tried that and dropped the profile into what I believe to be the correct place :- /home/clive/.mozilla-thunderbird/Profiles/9hrlsbn1.default

I now have all the folders from the installation on XP (.msf files) BUT when I fire up Thunderbird there's nothing?!?!:confused::confused:

Next trick?

---

### Post by ugm6hr on 2009-02-08
[http://users.telenet.be/mydotcom/howto/linux/migration01.htm](http://users.telenet.be/mydotcom/howto/linux/migration01.htm)

> rename it or set the correct folder name in $HOME/.mozilla-thunderbird/profiles.ini

---

### Post by Captain Legless on 2009-02-08
As can be seen from my previous post, Thunderbird is in the folder :- home/clive

I have tried cutting and pasting the *.mozilla-thunderbird* folder from that location and into */home* but the option to '*paste*' is greyed out and so unavailable.....as is 'ctrl V'.

Am I going about this the wrong way? I.E. should I be using the terminal window somehow?

---

### Post by ugm6hr on 2009-02-08
It is already in the right place.

I think you just need to tell T-bird to look for the correct profile.

I can't remember if this can be done from within T-bird (have a look in preferences).

The other option is to delete all other profiles - it should automatically pick up the only remaining one.

Or edit the settings in ~/.mozilla-thunderbird/profiles.ini

---

### Post by Captain Legless on 2009-02-08
Looks like I got there! I done basically what you've said but beat you to it.

I found that I had to remove the existing profile which comprised an apparent random name........djuxhpm2.default and replace it with the one coppied from the installation on XP.

I then had to edit the profile,ini file so that it pointed to the new file.

Voila...........success.

Thanks for the help - you pointed me in the right direction. =D>

---

