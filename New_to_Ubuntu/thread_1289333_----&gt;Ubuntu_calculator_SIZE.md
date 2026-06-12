---
title: "----&gt;Ubuntu calculator SIZE?"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by R3fr4cti0n on 2009-10-12
Any way to set a BIGGER default size for the ubuntu calc, i use a touch screen tablet and the defult size of the calc is to small for my fingers.
i hate that i have to keep adjusting it everytime i pull it up

---

### Post by HarrisonNapper on 2009-10-12
Well, you can write a script for it one way or another, but I would start by checking the home page or wiki of the calc you're using. They probably have the info there.

---

### Post by A_M_S on 2009-10-12
Try Devilspie

[http://help.ubuntu.com/community/Devilspie](http://help.ubuntu.com/community/Devilspie)

Hope it helps

---

### Post by sisco311 on 2009-10-12
Try [devilspie]("https://help.ubuntu.com/community/Devilspie").

[list]
[*]install it:
```
sudo apt-get install devilspie
```

[*]create the config directory:
```
mkdir ~/.devilspie
```

[*]create a config file for gnome-calculator:
```
gedit ~/.devilspie/gnome-calculator.ds
```

to start the app maximized, edit the file to something like:
```
(if (matches (window_name) "^Calculator.+")
  (begin
    maximize 
  )
)

```

to set a custom size:
```
(if (matches (window_name) "^Calculator.+")
  (begin
    geometry "1000x978+0+0"
  )
)

```

[*]save the file and exit.

[*]press Alt+F2, and run:
```
devilspie
```

[*]add devilspie to the start-up applications.

[/list]

---

### Post by Marlonsm on 2009-10-12
> **sisco311 said:**
> Try [devilspie]("https://help.ubuntu.com/community/Devilspie").

[list]
[*]install it:
```
sudo apt-get install devilspie
```

[*]create the config directory:
```
mkdir ~/.devilspie
```

[*]create a config file for gnome-calculator:
```
gedit ~/.devilspie/gnome-calculator.ds
```

to start the app maximized, edit the file to something like:
```
(if (matches (window_name) "^Calculator.+")
  (begin
    maximize 
  )
)

```

to set a custom size:
```
(if (matches (window_name) "^Calculator.+")
  (begin
    geometry "1000x978+0+0"
  )
)

```

[*]save the file and exit.

[*]press Alt+F2, and run:
```
devilspie
```

[*]add devilspie to the start-up applications.

[/list]

That could work, but maybe it'd be better to add the resize command to the calculator launcher...

---

