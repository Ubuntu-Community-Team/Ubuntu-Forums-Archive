---
title: "Desktop loads slower and slower after login."
date: 2009-04-06
forum: New to Ubuntu
---

### Post by kramer65 on 2009-04-06
Hello,

I've got Ubuntu 8.04 and I'm pretty happy with it. For the last few months however, the loading of the desktop seems to become slower and slower. After I typed in my username and password, it first always loaded in a few seconds. I just measured it and it now takes 48 seconds..

I don't load more programs at startup than I used to and I have no clue what the cause could be..

Any ideas?

---

### Post by metallicamike on 2009-04-06
do you have compiz turned on? that makes xorg take longer. also is your desktop customized? and have you gotton more apps/files? having more things makes your home directory longer to pull up.

---

### Post by kramer65 on 2009-04-07
My home folder and desktop indeed contain more files than they did before. But does that mean that it loads slower? I figured it doesn't need to load all those files since it only does so when it is going to use them.

Would it become quicker if I take things out of my home folder onto the external hard drive?

---

### Post by ibuclaw on 2009-04-07
If your desktop and desktop apps have grown in size, you could look into readahead your initial desktop files.
This is loading the files required for your Desktop to start into RAM before you begin to login, so it should speed up the login process, as it will get most data from RAM instead of from the Hard Drive, which appears to be the apparent bottleneck.

There is an excellent guide here: [http://ubuntuforums.org/showthread.php?t=565651](http://ubuntuforums.org/showthread.php?t=565651)

If you have any trouble following it, do post what you are unsure of.

Regards
Iain

---

### Post by kramer65 on 2009-04-07
Hi Tinivole,

Thanks for the suggestion. That looks quite advanced and not something for now. Primarily since this is my main working station on which I do not want to mess things up (which I did before already..).

On the next rainy sunday however, I will give it a go, since it really bothers me..

In a few weeks I also want to buy a netbook and I really want that to boot fast, so I'll definitely remember this post.

Thanks in advance!

---

