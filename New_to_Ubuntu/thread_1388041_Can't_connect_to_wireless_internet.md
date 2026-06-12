---
title: "Can't connect to wireless internet"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by sophie1983 on 2010-01-22
Hi I've been using ubuntu 9.10 on my laptop for a few months now. I have just moved house and in my old flat I could connect to the wireless internet without any problems. However in my new flat although I can 'see' my wireless network I can't connect to it. It just keeps asking for the WPA & WPA2 key which I type in then it asks for it again.

Any suggestions as to how to sort this out?

Thanks

Sophie

---

### Post by gordintoronto on 2010-01-22
It's possible that someone else in the new building is running a network on the same channel, or has other conflicting hardware.  Try setting your router to use a different channel.

---

### Post by NCLI on 2010-01-22
I know this sounds obvious and ridiculous, but are you absolutely certain you're entering the correct code? 

Does it take a while before it asks you again, or is it immediate?

---

### Post by alabasterjones on 2010-01-22
This same thing is happening to me...Both Windows XP and Mac OS 10.4 connect fine to the router, so it's not the router's fault and I'll be damned if I have to change anything for this computer since I am only setting it up to sell it. I just want to make absolutely sure that the wireless works, though I've had it working with Windows XP and previous versions of Ubuntu on this same computer...

---

### Post by warfacegod on 2010-01-22
Try using a passphrase that is only lower case. It sounds stupid but I've seen it work for a few people.

---

### Post by sophie1983 on 2010-01-25
I've tried entering in the WPA code lots of times. It waits for a while the asks for the code again. I've tried entering it with capitals and in lower case, but no luck so I'm sure its not me entering the code wrong.

The wireless was set up using a Mac, not sure if that could cause a problem. How would I change the channel the router is running on? 

Thanks for your suggestions and if you have anymore ideas they would be much appreciated! :)

---

### Post by warfacegod on 2010-01-25
Setting up your encryption key with a Mac or even a Windows machine will have nothing to do with your Linux machuine's ability to utilize it. What it sounds like to me is that your Network Manager isn't remembering the passkey correctly.

When I said try lower case what I meant was actually change the passkey into all lower case symbols.

Example:

Old key is:   8urLE2E7Gj

Go into your router summary and make the passkey

New key:    8urle2e7gj

---

### Post by sophie1983 on 2010-01-25
I have tried making the passkey all in lowercase (as in your example 'new key') and it still isn't working

---

### Post by Marvin666 on 2010-01-25
For a few minutes, could you set it to no security and see if it connects?

---

### Post by caravel on 2010-01-25
Are you connecting through network manager?  If so the issue is probably down to the encryption type.  Personally I've always had trouble with WPA2, try connecting via WPA and TKIP.  Go into network manager, delete any wireless connections there and start anew.

---

### Post by sophie1983 on 2010-01-29
I tried deleting all the wireless networks listed in my network manager, but that hasn't worked either. It keeps asking for the WPA code and I can't select the WEP key to input that instead.

---

### Post by lijcam on 2010-01-29
You could try deleting the default keyring.

source: [http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)

[LIST=1]
[*]Open up your Home Folder by clicking Places>Home Folder
[*]Press CTRL-H (or click View>Show Hidden Files)
[*]Find a folder called .gnome2 (it has a period at the beginning of the name) and open it by double clicking on it
[*]In side of the .gnome2 folder, there is another folder called keyrings.  Open it up.
[*]Delete any files you find within the keyrings folder
[*]Restart the computer
[/LIST]
After you restart and login (if you’re automatically logging in) you’ll probably be asked to enter your wireless networks WPA/WEP encryption key.  After you type that password in, the keyring manager will appear to let you know that it would like to handle the storage of that password.

---

