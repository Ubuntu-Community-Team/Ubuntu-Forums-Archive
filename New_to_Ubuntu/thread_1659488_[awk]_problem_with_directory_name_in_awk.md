---
title: "[awk] problem with directory name in awk"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by Farah_online on 2011-01-04
Hi ... 

I am trying to write a script that takes 2 arguments :  the first file contain some files extensions , and the second a  directory . 
  My script move the files which their extension existed in the extension's file to the directory.
  This is my script: 
  
```

BEGIN{ } 
{  
   file_ext = $1  
   folder = $2  
   isexist = "[ -e " $1 " ]"  
   if( ( system(isexist) ) != 0 )  
   {  
        getline < file_ext   
        system("find *." $0" -exec mv {} " folder " \;")    
        next  
   } 
} 
END{ } 

```But when I call the script in the shell , I am getting this error :
mv: missing destination file operand after `koko.cpp'
 When I put folder name directly it works fine , but when I pass it by argument it doesn't work, why?

---

