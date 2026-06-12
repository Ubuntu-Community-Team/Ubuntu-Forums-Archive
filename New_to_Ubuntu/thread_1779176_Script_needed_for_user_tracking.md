---
title: "Script needed for user tracking"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by digitography on 2011-06-10
I am hoping that there are folk out there far smarter than me who can offer a quick and easy solution to this.

OK, I have a small resource centre a mixture of Windoze and Ubuntu. Users have a generic login, ie everyone uses the same. At login I want a page or window that will ask for the users name, note the time, and log that information into a file of some description. My thinking is that this could be done with Javascript, I'm no programmer, although I can bodge things together, but I'm thinking there must be something of this nature out there.

Thanks

---

### Post by hakermania on 2011-06-10
Nono, this is much more easy way:
Make this script:
```

#!/bin/bash
szAnswer=$(zenity --entry --text "Please input your name" --entry-text "Name Here");
echo "$szAnswer $(date '+%r %d.%m.%Y')" >> /path/to/log

```Make the script executable and open the StartUp Applications program. Insert this script there and you're done.
Now, anybody who logs in will give his/her username and it will be logged to a file.
If you want to have specific names for input (e.g. you don't want inputs like 'house' and 'dog' but only 'alex' and 'mary') then you can have a case statement:

```

case $szAnswer in
      alex|mary|markos|anthony)
            echo "$szAnswer $(date '+%r %d.%m.%Y')" >> /path/to/log;;
      *)
            zenity --info --text "Invalid name specified, try again";;
esac
```the complete code would look like:
```

#!/bin/bash
a=0
while [ $a -eq 0 ]; do
szAnswer=$(zenity --entry --text "Please input your name" --entry-text "Name Here");
case $szAnswer in
      alex|mary|markos|anthony)
            echo "$szAnswer $(date '+%r %d.%m.%Y')" >> /path/to/log
             a=1;;
      *)
            zenity --info --text "Invalid name specified, try again";;
esac
done

```instead of the $a you could also use 'break'

---

