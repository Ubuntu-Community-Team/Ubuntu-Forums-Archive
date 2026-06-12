---
title: "scripting help"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by rburkartjo on 2009-10-07
note i am running a script thru the terminal. what line would i add to have it minimize (the terminal) after it is executed. tks

---

### Post by trigsenior on 2009-10-07
Not sure i understand , 

You can run a script in back ground with & option

so 

```
./script &
```

OR if you want to be notfied once the script is done add this to within  script  

```
notify-send "The script has finished"
```

OR play around with 

```
 gnome-terminal --zoom=.5 
```

not in a gnome envirorment , so not sure if it will do what you want

---

### Post by rburkartjo on 2009-10-08
trig tks ref the background option where should that go at the beginning of the script or the end

---

### Post by Sarmacid on 2009-10-08
Just put it in with the line where you run the script. As trig put it ```
./script &
```

---

### Post by NoaHall on 2009-10-08
Or use "exit" in your script to close it.

---

### Post by unutbu on 2009-10-08
rburkartjo, if you really want to minimize the window, you can do it by installing the wmctrl package. The command 
```

wmctrl -r :ACTIVE: -b add,hidden

```
minimizes the active window, and 
```

wmctrl -r "rburkartjo" -b add,hidden
```

would minimize the first window whose title contains the string "rburkartjo".
Usually terminals are titled "username@host dir", so the above command would probably minimize the terminal. We'd have to think of a workaround (like retitling the terminal at launch time) if you have multiple windows entitled "rburkartjo".

---

### Post by rburkartjo on 2009-10-10
tks

---

