---
title: "evolution error says &quot;error loading address book&quot;"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by stinger30au on 2009-12-20
the full message is as follows
====================================================
Error loading address book.

This address book cannot be opened.  Please check that the path (null) exists and that permissions are set to access it.

Detailed error message: Other error
====================================================

the main reason i believe it is doing this is because the emil settings were backed up from a 9.10 and installed to 9.04

9.10 has the "cloud" or ubuntu1 feature.
9.04 doesnt have this

if i boot the pc with a 9.10 cd and restore the evolution data i can see the address book and all is well.
if while i have the address book open in 9.10 that i booted from cd and save a contacts a a vcard and import it , it says it imported it, and gives no errors and you cant see any contacts listings.

any ideas?
thanks

---

### Post by stinger30au on 2009-12-21
i *MIGHT* have found an answer

[http://ubuntuforums.org/showthread.php?t=688911](http://ubuntuforums.org/showthread.php?t=688911)

need to test it

---

### Post by stinger30au on 2009-12-21
ok, fixxed it

fist part of the fix is to repair the corrupt contacts
from this post
[http://ubuntuforums.org/showthread.php?t=688911](http://ubuntuforums.org/showthread.php?t=688911)

do this

- close Evolution
- delete /home/username/.gconf/apps/evolution/addressbook (it will be recreated)
- delete /home/username/.evolution/addressbook (it will be recreated)
- reboot your computer (this is crucial, otherwise the faulty gconf files will be restored)
- launch Evolution and enjoy your working address book



now, when i did this, the address book is fixxed in the fact it does not give an error but all email contacts are deleted

sssssooooo

i rebooted with 9.10 cd and disconnected router from pc and started evolution and told it to restore from backup, this way i can get access to the email address book 

once evolution is started we want to back up all the addresses only and save so we can import in to 9.04 that boots of hdd

so do this

open evolution
click contacts
edit select all
file - save address book as vcard (it will save it as list.vcf)
(save the file to somewhere u can access after pc boots backup off hdd)

now tell the pc to reboot and remove the 9.10 boot cd

now pc boots up in 9.04 off hdd and again restart evolution and we will now import mail contacts

start evolution
click contacts
file -import-forward-import single file
point it to the list.vcf file
tell it to import to "personal"

done!

all email contacts are fully restored and it works fine

---

