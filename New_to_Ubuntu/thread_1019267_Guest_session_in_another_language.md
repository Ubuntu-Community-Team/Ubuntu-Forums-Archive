---
title: "Guest session in another language"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by ubuntu27 on 2008-12-22
Hello everyone. I am seeking your help.

I need to know how to choose the language that should be used inside the guess session. 
Currently, my user (which has the ability to use sudo) uses US English, but I want the Guest session to use Spanish.

Is there anyway to accomplish this?

Thank you in advance!! :D

---

### Post by nhasian on 2008-12-23
I dont know if you can change the default language for the guest session but you can definitely create a user for them and set the language & keyboard layout preferences for that user.

---

### Post by ubuntu27 on 2008-12-24
Thank you nhasian. I went to LaunchPad and filled a bug. But they told me that this is a feature request so I should go to Ubuntu Brainstorm.

Anyway, I will do that later.


Thank you again.

---

### Post by mkvnmtr on 2008-12-24
In my browsers and for that matter I enable english and spanish. I also have both keybords enabled to switch between them.Would that not be enough or would you need all the instructions in the other language?

---

### Post by petyabest on 2012-10-14
This is the procedure in Ubuntu 12.04:

1. Let's create a single account. In the user account's setup we can change the default language for the account. (let's the username for this example 'guest', but you can use any other name too.)

2. Create a guest-session directory in the /etc
> sudo mkdir /etc/guest-session

3. Copy our newly created single user account's home to /etc/guest-session.
> sudo cp -R /home/guest /etc/guest-session

4. Rename our directory to 'skel'
> cd /etc/guest-session; sudo mv guest skel

5. Remove the our temporary 'guest' account from the account list. We can remove all files too. (Remove our single user named in this exampla 'guest'.)

6. Make a new login to the built-in guest account.

The guest account appear in the other language.

If we want to clear this setup, just simply remove the 'guest-session' directory from /etc
> sudo rm -rf /etc/guest-session

In this way we can make any setup in the guest-session.

---

