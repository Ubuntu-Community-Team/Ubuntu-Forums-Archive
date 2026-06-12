---
title: "Hiding info in images..."
date: 2009-01-15
forum: New to Ubuntu
---

### Post by baracuda68 on 2009-01-15
Hi.
I stumbled upon this: [http://www.techsnack.net/how-to-hide-important-information-in-an-image-file](http://www.techsnack.net/how-to-hide-important-information-in-an-image-file)

How would I do this in Linux and what do you think of this practice?

Thanks.  Bob :guitar:

---

### Post by blueridgedog on 2009-01-16
In Linux you could 

```
cat mytextfile.txt >> myimage.jpg
```

or 

```
echo "my password is bar" >> myimage.jpg
```

(not certain of the syntax on the last one...on

In command line parlance, > means "goes into".  > overwrites and >> appends.  I think the trick described works because the image viewer gets the header and data right and notepad ignores the binary data.  I don't think a Linux text editor would only display the text portion.

---

### Post by baruch60610 on 2009-01-16
There are a variety of ways to do this.  Probably one of the simplest is to make a copy of an image, and another image of the same size containing the message (in black text on a white background).  Perform a byte-by-byte function on the two files.  When the message file contains a black bit, change the value of the image bit by incrementing it by one.  Save this bitwise comparison as third image.

When you want to decode the message, you can do a bytewise XOR with the original (non-message) image, and the one you created.  All the bytes that are identical will be zero.  The ones that were changed will be non-zero.  You can save the results as another image that will contain the message.

The description in the article you linked to is another way to do it, but it suffers from being easily discovered if someone accidentally tries to open the image in the wrong manner.  Blueridgedog's example would work, though.

Using kate I got a whole bunch of binary stuff, with the message at the end.  It worked, but it's not pretty.

But probably your safest bet is to use a security program to encrypt the text with a password.  Using mcrypt, you can simply say:

mcrypt secret.txt

When you do that, you'll be asked for a passphrase.  Enter something you'll remember, but that could be hard to guess.  A passphrase can contain spaces, unlike a password.  You'll need to enter it twice, to make sure you typed it correctly.  Now your text is encrypted as a file secret.txt.nc.  You can remove the original, plaintext file and rename secret.txt.nc to something like 'photo.jpg', if you like.

All of this is fine, but unless you're sharing your directory with someone, it's more work than necessary.  If you've got different users, then you can simply use the chmod program to change the read attributes so that no one other than the user can read the text.  You can put it into a directory also protected by chmod.

So, put 'secret.txt' into a directory like /home/user/math (something boring-sounding).  Then cd into that directory and type:

chmod 0600 secret.txt

or whatever you named the file.  That makes it readable (and writeable) only by user (which should be you).

cd up out of that directory, and then type:

chmod 0700 /home/user/math

That will make the directory un-listable by anyone but user.  They won't be able to cd into it, nor even see whether there are files in there.

---

