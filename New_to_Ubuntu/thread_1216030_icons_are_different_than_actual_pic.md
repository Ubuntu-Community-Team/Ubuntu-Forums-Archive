---
title: "icons are different than actual pic"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by kmsomers on 2009-07-17
[SIZE=3]Hello everyone[/SIZE]

    [SIZE=3]I have been having an issue with my pictures once I put them into a folder.Since my Olympus camera numbers the pics, when I add more pics to the folders, the picture on the "thumbnail" is not the picture when I double click the thumbnail. How can I get this to show the proper picture all the time? I'm running the latest version before 9.04 ( scared to update HA!) Not sure what other info is needed.[/SIZE]

[SIZE=3]Thanks

Kevin[/SIZE]

---

### Post by kmsomers on 2009-07-18
[SIZE=4]Anyone have this happen to them?[/SIZE]

[SIZE=4]Kevin[/SIZE]

---

### Post by kmsomers on 2009-07-25
[SIZE=4]I've upgraded to 9.04 with no change in the thumbnails. The pic you see, is not what you see when you double click on it??[/SIZE]

---

### Post by LewRockwell on 2009-07-25
I've seen similar occurrences but I don't have an explanation

.

---

### Post by credobyte on 2009-07-25
```
cd $HOME && sudo rm -r .thumbnails/*

```

Use at your own risk ( deletes all thumbnails and upon browsing to your pic folder, will generate them again, hopefully, without any mistakes ).

---

### Post by kmsomers on 2009-07-25
[SIZE=3]Thanks for the replies... I would rather not try something "at my risk" so for now,I'll deal with it.[/SIZE]
[SIZE=3]
Thanks

Kevin[/SIZE]

---

### Post by Crunchy the Headcrab on 2009-07-25
I don't think it's really dangerous.  It just means that instead of loading instantaneously the pictures will have to be generated again the FIRST time that you look at the folder.  Then they should be fine from then on.  (think cleaning cache)

---

### Post by credobyte on 2009-07-25
> **kmsomers said:**
> [SIZE=1]Thanks for the replies... I would rather not try something "at my risk" so for now,I'll deal with it.
[/SIZE] [SIZE=1]
Thanks

Kevin[/SIZE]

Sorry if I scared you - previously posted command will simply delete your thumbnail cache ( like a permanent temp folder ) and once you'll browse to a folder with pictures, Ubuntu will re-generate them, hopefully, in the right order ( 99% success rate ).

---

### Post by kmsomers on 2009-07-27
[SIZE=3]Great, that sounds better! I'll give it a try...[/SIZE]
[SIZE=3][/SIZE] 
[SIZE=3]Kevin[/SIZE]

---

### Post by vinutux on 2009-07-27
delete local thumbnail catch ```
rm /home/[COLOR="Red"]yourusername[/COLOR]/.thumbnails
```

or delete this manually in press ctrl+H in home folder and delete .thumbnails folder

---

### Post by kmsomers on 2009-07-27
[SIZE=3][SIZE=2]> **credobyte said:**
> ```
cd $HOME && sudo rm -r .thumbnails/*

```Use at your own risk ( deletes all thumbnails and upon browsing to your pic folder, will generate them again, hopefully, without any mistakes ).
[/SIZE]

  This command didn't want to run. "command not found" for some reason in the terminal.[/SIZE] 
 [SIZE=3] So I tried the other suggestion "ctrl+H and delete .thumbnails folder. This worked perfectly! Thanks for the all the help guys. I'm not sure what I did or why it worked like that , but it seems to be gone!!

You guys are awesome help!!

Kevin[/SIZE]

---

### Post by vinutux on 2009-07-28
> **kmsomers said:**
> [SIZE=3][SIZE=2]
[/SIZE]

  This command didn't want to run. "command not found" for some reason in the terminal.[/SIZE] 
 [SIZE=3] So I tried the other suggestion "ctrl+H and delete .thumbnails folder. This worked perfectly! Thanks for the all the help guys. I'm not sure what I did or why it worked like that , but it seems to be gone!!

You guys are awesome help!!

Kevin[/SIZE]

This is because your thumbnail cache is currupted....delete them means it re-cache all thumnail data....so itz worked perfectly......

---

### Post by kmsomers on 2009-07-28
[SIZE=4]Thanks Again!![/SIZE]
[SIZE=4][/SIZE] 
[SIZE=4]Kevin[/SIZE]

---

