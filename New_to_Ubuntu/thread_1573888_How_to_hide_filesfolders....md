---
title: "How to hide files/folders..."
date: 2010-09-13
forum: New to Ubuntu
---

### Post by Rician on 2010-09-13
how do i hide these $RECYCLE.BIN, system volume information,.Trash-1000 folders?

how do i hide files/folders i dont want to see?

or should i just delete these files???

---

### Post by CharlesA on 2010-09-13
You can set files to be hidden by adding a dot (.) to the beginning of the filename.

However, you are dual booting something with Windows, it'll freak out if you rename $RECYCLE.BIN to .$RECYCLE.BIN. Same with system volume information.

---

### Post by warfacegod on 2010-09-13
Try hitting Ctrl+H. It sounds like you have "Show hidden folders" enabled. If that isn't enabled, you can try renaming the folders and putting a period in front of the name. Like this: .foldername

---

### Post by Rician on 2010-09-13
i am not duel booting windows i only have ubuntu and my removable drives. but these folders/folders appear in all my removable drives too. its so annoying to see them.

 Thanks all for help. i dont see them files anymore now.

---

### Post by warfacegod on 2010-09-13
Those Recycle Bin folders are probably there from the drives being used in Windows. In Windows each separate hard drive (removable usb's count as HDD's) gets its own recycle bin folder. Pretty sure Linux is the same way.

---

### Post by fly-by-night on 2010-09-13
Make a file named **.hidden** and place all the folder names you want to hide - one per line - save and refresh.  The file must be in the main folder of the subfolders you want to hide.

Edit: you can delete all the Windows system directories. The minute you connect it to a Windows machine it will be back.

---

### Post by CharlesA on 2010-09-13
> **fly-by-night said:**
> Make a file named **.hidden** and place all the folder names you want to hide - one per line - save and refresh.  The file must be in the main folder of the subfolders you want to hide.

Edit: you can delete all the Windows system directories. The minute you connect it to a Windows machine it will be back.
Interesting.

Thanks for the info on that! :)

---

### Post by warfacegod on 2010-09-14
The same thing applies to Ubuntu's .trash folder as well.

---

