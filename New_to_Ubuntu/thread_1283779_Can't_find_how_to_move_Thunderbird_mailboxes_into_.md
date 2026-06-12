---
title: "Can't find how to move Thunderbird mailboxes into Ubuntu"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by hazypictures on 2009-10-05
I've been using Ubuntu for 3 days now and have had amazing help from this forum. Thank you.

I am a refugee from Vista where I used Thunderbird for email. I have installed version 2.0.0.23 on Ubuntu but cannot figured out how to get my address book and message history into my new setup.

Any tips? I tried moving the folder but it doesn't show up in Thunderbird.

Thanks.

---

### Post by Hospadar on 2009-10-05
I'm not sure about your messages (i know there's a way, but I've never done it so I can't say) but as for address book, you can go to Tools->Address Book->Tools->Export (in vista) then in ubuntu, go Tools->Address Book->Import and import the thing you exported

---

### Post by oldfred on 2009-10-05
I use a shared partition for both Tbird and Firefox. I also converted firefox in both windows & ubuntu from 2 to 3 to 3.5. I have not tried the proposed new thunderbird yet with my shared profile.

Start Thunderbird & shut down. In place, homefolder, (change view setting check to show hidden files), scroll down to .mozilla-thunder
on my system:

/home/fred/.mozilla-thunderbird

It should contain a profile file and a directory xxxxxx.default
You can copy the entire default directory from one computer to another. If the name or path is different you can edit the profile with the correct entry. I also copy my shared to my portable and back when I travel without any problem.

More info:
[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)
[http://kb.mozillazine.org/Category:Profiles](http://kb.mozillazine.org/Category:Profiles)

You can also have mutiple profiles by starting tbird in the terminal or editing the icon.
```
thunderbird %u -Profilemanager
```

---

