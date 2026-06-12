---
title: "Error message at top of screen"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by scifisam on 2010-01-26
Folks,
I have a red circle with a white line across it at the top of my window.When I click on it I get the following  E:malformed line62 in source listetc/apt/sources.list  [URI parse]
I think I caused the error by following instructions on ten things you must do after installing Ubuntu 9.10 located at URL  file://media/7E74AB2B74AAE55D/Documents and settings.

Could someone please help me fix this.

 Tanks Sincerely Scifisam <mrmarks@juno.com> or <blackbird-green@hotmail.com>

---

### Post by jd65pl on 2010-01-26
Can you post the file /etc/apt/sources.lst?

If you run the following command in the terminal it will put the contents in a file called sources.txt in your home directory to upload. Someone will then be able to help you further.

```
cat /etc/apt/sources.list > ~/sources.txt
```

---

### Post by Paqman on 2010-01-26
You might want to remove your email address from that post, posting your email addy on a public forum is a bit of a spam magnet. People can send you email through your account on this forum.

---

### Post by scifisam on 2010-01-26
Thanks for the heads up

---

### Post by scifisam on 2010-01-26
What do you mean by post the file?

---

### Post by jd65pl on 2010-01-26
Attach the file to a message on this forum, you will see the 'Attach files' option below when you reply to a message in the 'Addition Options' section.

Alternatively just add the contents of a file as a reply to this thread.

---

### Post by hhlp on 2010-01-26
> **jd65pl said:**
> Can you post the file /etc/apt/sources.lst?

If you run the following command in the terminal it will put the contents in a file called sources.txt in your home directory to upload. Someone will then be able to help you further.

```
cat /etc/apt/sources.list > ~/sources.txt
```

execute that command and upload that file

---

### Post by scifisam on 2010-01-26
Folks,
Is there anyway to repair my installation without removing and re installing the whole buisness?My error saysE:malformed line 62in sourcelist/ect/apt/sources.list [URI] E:The list of sources could not be read

  Tahnks Scifisam;)

---

### Post by audiomick on 2010-01-26
When did you get the error?

---

### Post by sisco311 on 2010-01-26
What's the content of the /ect/apt/sources.list file?

```
cat /ect/apt/sources.list
```

---

### Post by bodhi.zazen on 2010-01-26
> **scifisam said:**
> Folks,
Is there anyway to repair my installation without removing and re installing the whole buisness?My error saysE:malformed line 62in sourcelist/ect/apt/sources.list [URI] E:The list of sources could not be read

  Tahnks Scifisam;)

yes, you need to edit /etc/apt/sources.list

Run this ```
gksu gedit /etc/apt/sources.list
```

post line # 62 (or the entire contents if you need to)

To see just line 62 :

```
cat -n /etc/apt/sources.list | grep 62
```

---

### Post by jd65pl on 2010-01-26
Double post [http://ubuntuforums.org/showthread.php?t=1391004](http://ubuntuforums.org/showthread.php?t=1391004)

---

### Post by jd65pl on 2010-01-26
@Scifisam no one is able to help you unless they can interpret the error, this involves you showing what is in that file, there is a problem with line 62 but it is not possible to tell you how to fix it without more information.

The problem you are having is not serious and can be fixed you just need to tell us what the file contains.

---

### Post by scifisam on 2010-01-26
> **scifisam said:**
> Folks,
I have a red circle with a white line across it at the top of my window.When I click on it I get the following  E:malformed line62 in source listetc/apt/sources.list  [URI parse]
I think I caused the error by following instructions on ten things you must do after installing Ubuntu 9.10 located at URL  file://media/7E74AB2B74AAE55D/Documents and settings.

Could someone please help me fix this.

 Tanks Sincerely Scifisam <mrmarks@juno.com> or <blackbird-green@hotmail.com>
I fixed this problem myself by booting to windows xp pro sp3 and going to the disk mngr and deleting all the unknown partitions and then re installing ubuntu9.10.

It works great now.And after searching so many "experts" they hadn't a clue how to uninstall ubuntu

---

### Post by scifisam on 2010-01-26
> **jd65pl said:**
> @Scifisam no one is able to help you unless they can interpret the error, this involves you showing what is in that file, there is a problem with line 62 but it is not possible to tell you how to fix it without more information.

The problem you are having is not serious and can be fixed you just need to tell us what the file contains.
please read my solution.Maybe you can help me though I can't seem to get access to my floppy drive even after downloading the right recommended driver.

---

### Post by Cheezespread on 2010-01-26
> **scifisam said:**
> I fixed this problem myself by booting to windows xp pro sp3 and going to the disk mngr and deleting all the unknown partitions and then re installing ubuntu9.10.

It works great now.And after searching so many "experts" they hadn't a clue how to uninstall ubuntu


The folks here were trying to give you an option which excluded anything related to Uninstalling Ubuntu.They have repeatedly asked to you provide the contents of the file **sources.list** by executing the command in the terminal.

---

### Post by jd65pl on 2010-01-27
> **scifisam said:**
> please read my solution.Maybe you can help me though I can't seem to get access to my floppy drive even after downloading the right recommended driver.

Your solution was far too drastic I wouldn't recommend anyone else with a similar issue do the same, it could have been fixed simply and quickly if the contents of the file were known.

Do you have a disk in the floppy drive? Where are you looking for it to me mounted? What is the driver you downloaded? it should be mounted to:

```
/media/floppy
```

---

