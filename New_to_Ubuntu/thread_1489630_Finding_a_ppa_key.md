---
title: "Finding a ppa key"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by expatCM on 2010-05-21
I went [here]("https://help.ubuntu.com/community/ThunderbirdNewVersion") and added ppa:ubuntu-mozilla-daily/ppa to the software sources.

I then ran sudo apt-get update and there was an error message.
```
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE
```

What is the proper way of finding this key, or any key for that matter?  Google does not seem to be the best way since I found this [link]("http://ubuntuforums.org/showthread.php?p=8514461") which gives the key and how to install ....  but I guess it is now out of date since whilst the key is there and can be added without error I still get the same error message.

So what I really would like to know is how to do this properly ...

---

### Post by sisco311 on 2010-05-21
When you add the ppa to the Software Sources the key is automatically downloaded and added to the list of trusted keys. Did you get any error messages?

Try to add it manually:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys **247510BE**
```

where **247510BE** are the last 8 characters from the public key's id.

See: [https://launchpad.net/+help/soyuz/ppa-sources-list.html](https://launchpad.net/+help/soyuz/ppa-sources-list.html)

---

### Post by -humanaut- on 2010-05-21
You can generally "drap & drop" keys into the software sources GUI as well.

---

### Post by expatCM on 2010-05-21
Thank you for the replies.

I ran the command at a terminal and the key was imported again.  Then ran sudo apt-get update and no errors appeared so I think this was a success.

I also took a look at the linked article (thank you).

So it seems that there are two ways of approaching this.  Either

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys last8chars

or 

sudo add-apt-repository ppa:user/ppa-name

I am pleased to now know the correct way to approach this. Thanks for the help.

---

