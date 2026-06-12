---
title: "why can't i decypt my files anymore?"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by super kim on 2010-05-10
so i made a key and i exported it first so it's backed up. then i encrypted my stuff, then i decrypted it to check it all worked before i removed the originals. then i removed the original files leaving only the encrypted files. then i was prompted by the update manager to update some stuff. so i did. so...

so why can i no longer decrypt my stuff, i had copied the key in case something went wrong, but it keeps saying my pass phrase is wrong. i know it's not wrong as i had tested and it's a password i know. i have tried importing the backed up key, but no success.

please help me out, i have tried to be sensible and encrypt and back up my personal files however they are useless to me unless i can decrypt them.

i don't really know about pgp or encryption but i have the key, and the passphrase however it won't work.

there is one good thing though, the files were on a removable hard disk and i've not used it much since i deleted the files, is it possible to recover them?

---

### Post by gzarkadas on 2010-05-10
First check the trash of your hdd. It is a folder typically named `.Trash-0'. You must enable `Show hidden files' option from the `View' menu of Nautilus.

When typing the passphrase, check that the language you use is the correct one and the keyboard mappings are the same as those you used when you created the passphrase. This is most relevant if you have a localised version of Ubuntu, ie not the English one.

You may also try to review the dpkg logs to see what did you installed before the ability to decrypt your files vanished and search for bug reports like yours in the packages web pages.

Also, there is a slight possibility that one of the keys of your keyboard may not be as sensitive as before due to mechanical reasons (something slipped in the gap space) and thus you lose a char in your passphrase. Open a text editor and type many times all the letters contained in your passphrase and see if some occasionally is missed. It may sound improbable, but it did happened to me.

---

### Post by super kim on 2010-05-11
There is no trash folder as it's an external drive there is no trash can. i can type the passphrase out fine with the keyboard.
this is the reason why encryption is dangerous, the worst thing is they are original documents and irreplaceable. i think i have been sensible but still the risk is that if your key or decryption software thingy breaks then the files that are so important become useless. pgp sucks

how can i recover deleted files, and don't say you can't with linux because the fbi can and do recover deleted files all the time. i've not written anything to the drive since i deleted the files so is it possible?

---

### Post by gzarkadas on 2010-05-12
Well you can't easily, that's for sure (see the [Ext3 FAQ]("http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html"), question #7). You can however use software that searches blocks of the device, such as forensic to read and recover unwritten blocks. You can try:

[LIST]
[*][TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") and [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec"). See this [article]("http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive") that describes an actual recovery done with these tools.
[*][Autopsy and Sleuth Kit]("http://www.sleuthkit.org/"). These are forensic tools; they are perhaps more inconvenient for batch undeleting a lot of files but maybe more powerful in recovering (some part of) badly damaged files. They are available as autopsy and sleuthkit packages at the universe repository.
[/LIST]
Your other option is to try solve the cryptographic software issue (say: downgrade to the previous version that worked for you or make a complete removal and re-install) and access your encrypted data.

---

### Post by super kim on 2010-05-14
thanks gzardkardas. i installed the TestDisk from the synaptics and ran PhotoRec. I got some of the important stuff back... and over 200gb of files i deleted years ago. i might need to run it again as i'm not sure if it finished. i accidentally pressed log-out instead of lock-screen, doh. it took nine hours so i'll wait till after the weekend to go again but fingers crossed i'll get it all back.

two things i've learned from this: 1, never delete unencrypted original documents. 2, delete doesn't mean delete, more like, don't see it and if you need the room overwrite it.

and i still think pgp sucks, so if anyone can explain why it doesn't then feel free. otherwise it sucks.

---

