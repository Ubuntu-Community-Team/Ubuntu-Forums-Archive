---
title: "Am I able to use undescores in file paths."
date: 2009-10-05
forum: New to Ubuntu
---

### Post by millertime on 2009-10-05
I am getting an error in terminal when trying to change my directory to anything with underscores, its telling me the folder does not exist, it clearly does I can see it when pulling the directory using the "ls" command, and I can see it in my folder manager?

I am thinking the underscore is not ideal for folder names anyway, I think I am going to clean this up as the more I use terminal the more annoying it gets, same with capital letters.

Thanks

---

### Post by tom.swartz07 on 2009-10-05
If you are having a problem with the titles, try encapsulating the entire path in quotation marks. for example, ```
cd "/home/my folder/another folder/"
```

The quotation marks mark off that it is one path, rather than an extra command.

---

### Post by tom.swartz07 on 2009-10-05
I just noticed that you mentioned about capital letter titles too. You could also use the {tab} key to autocomplete the locations or commands that you are typing.

```
cd ~/Des
```
Then hit tab, and you get
```
/home/USERNAME/Desktop/
```

Its just a cool little shortcut.
There are quite a few tutorials about terminal and bash commands. Try Youtube, or a quick Google search.

Hope this helps!

---

### Post by credobyte on 2009-10-05
You can use as many underscores as you want.

---

### Post by millertime on 2009-10-05
I don't know why I didn't try quotes. That is child stuff, thanks a lot.

---

### Post by ad_267 on 2009-10-05
> **millertime said:**
> I don't know why I didn't try quotes. That is child stuff, thanks a lot.

You shouldn't need quotes for a file name with underscores. Usually I use underscores instead of spaces because it's easier to deal with from the command line.

---

### Post by tom66 on 2009-10-05
Most Linux filesystems allow all characters except NULL (0) or '/'. 

If you want, you can also put slashes before each character to escape:

~/My\ Videos/

is the same as

"~/My Videos"

and

"/home/thomas/My Videos"

---

