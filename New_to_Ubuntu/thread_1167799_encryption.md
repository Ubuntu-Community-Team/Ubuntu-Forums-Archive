---
title: "encryption"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by mojolobo on 2009-05-23
Hello everyone

I was wondering about a feature in my 9.04.

When i right-click a file , there is an option to encrypt. When i click it " No encryption keys were found..." And it starts the encryption & keyring program. Every tab is empty except passwords : login.

I have no encryption software installed, i have no idea how this works.

My questions are 
How do i use this feature?

Do i need to install encryption software?

thank you

---

### Post by mcduck on 2009-05-23
You already have all the programs required, now you'll just have to create your personal encryption key. :)

Go to Passwords and Encryption Keys, select File/New and then "PGP Key". Now enter your information and click "Create" and wait while the encryption key is generated. That may take a while.

After the key has been created you will be able to encrypt files from the right-click menu.

---

### Post by lukjad on 2009-05-23
Go to *System->Preferences->Encryption and Keyrings*. That is where you need to set up the encryption I think.

---

### Post by fmfrisch on 2009-05-23
Ok. So I don't know if you would call this a bug but this is how it works. When you right-click and choose encrypt, at least in 9.04, it always says that there are no keys. However if the seahorse (Password & encryption keys) software is running it will be able to detect your keys and so with that application running right-click again and press encrypt.

This only works if you already have keys imported into the seahorse application though. If you have no keys you will have to first, create your own key (not necessary, however it is very good to have) secondly import the key of the person who will be decrypting the file. This could be you own key if the encryption is just for you. All this can be done in the Seahorse application that comes with Ubuntu by default. You can find it under accessories. It has the name Password & encryption keys in the menu.

No install of other software is needed just the import/creation of PGP keys. But if you are looking to encrypt files that are staying on your local machine I would not suggest PGP because whoever gets a hold of your file could probably get a hold of the key to decrypt. For encryption of local files I would suggest a application such as Truecrypt or similar. There are a few out there. Google it!

/fmfrisch

---

### Post by mojolobo on 2009-05-23
It worked .

Will also download truecrypt , and give it a go.

Thanks again.

---

### Post by bedouinfred on 2009-06-01
I have gpg installed, plus good keys.  After upgrading to jaunty, i get the message "Decryption failed you probably do not have the decryption key".  
Also, when I right click and try to encrypt, i get the dialog box to choose a recipient, while all i want to do is to encrypt a file for my use.

What can cause this?

---

### Post by unutbu on 2009-06-01
I believe to encrypt a file you are using the public key.  To decrypt the file
you would need the private key.

So it sounds like you might be missing the private key. Private keys are kept in a file called ~/.gnupg/secring.pgp, public keys are in ~/.gnupg/pubring.gpg.

---

