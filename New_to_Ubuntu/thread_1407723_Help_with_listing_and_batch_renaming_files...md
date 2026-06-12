---
title: "Help with listing and batch renaming files.."
date: 2010-02-15
forum: New to Ubuntu
---

### Post by dagarshali on 2010-02-15
Hi
I have saved files, the names of which are the time steps during a simualation. Now i need to list files between two particular time steps..how do i it. I further need to use the listed files and rename into 1,2,3 etc for using them to make a movie.

currently i used the following bash script to rename the files in 1,2,...
The problem is it does for all the files in the directory..I need it for a certain range.

#! /bin/bash 
filenum=1
for dir in ` ls -1`
 do
  cp  $dir/U* ../U_files/U_${filenum}.vtk
  let filenum=filenum+1
done

Any help ?

Regards,
vishwa

---

### Post by kaibob on 2010-02-15
It's difficult to answer your question without some information as to how the source files are named. However, in general, you would probably extract the numerical "time stamp" data from the source file names and then test that data against time-from and time-to parameters that you could imput as command line arguments. Thus the test to be inserted in your existing script might be:

```
if [ "$time" -gt $1 -a "$time" -lt $2 ] ; then
   echo "$time"
   cp $dir/U* ../U_files/U_${filenum}.vtk
fi
```

Anyways, the above is just a best guess based on the information you provide but hopefully will be a starting point for you.

---

