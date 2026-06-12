---
title: "Help needed on the bash script"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by neoknight on 2009-03-09
Hi All,

I am planning to delete few files from a subdirectory, my aim is to locate all *.des files, remove them all except the one which the user specifies.here is the code i wrote which is not coming out right. des1 is already existing in the folder, and i am copying that to a new file with a different name and deleting all the *.des files in that folder.

one more thing is, that there are also other type of files in the directory. so i just want to remove only the *.des files keeping the only one which the user specifies.

#!/bin/bash
echo "Enter Des File name"
read des1
echo " Enter the 5 digit name"
read des2
cp $des1 $des2
touch $des2
for i in `ls .`
rm -f $i/*.des

i know that above code removes all *.des files, wat command do i add to exclude that particular user given file.

if you point me to the command name , i will figure out the code...

Thanks

---

### Post by blueridgedog on 2009-03-10
I would rename the user specified file prior to the rm, then change the name back afterworlds.  This would be a simple alternative.

---

### Post by xzero1 on 2009-03-10
Never tried it in this context, but grep might be of use here.

---

### Post by Cappy on 2009-03-10
```
#!/bin/bash
cd $i
filenames=*.des
filenames=`echo ${filenames//$des2/}`
rm $filenames
```

using bash expansion and then using bash to substitute, similar to sed s/hay/replacement/g
Extra white space doesn't matter

Your code doesn't make any sense to loop through everyfile when bash is expanding the names of the file to delete anyway.

---

