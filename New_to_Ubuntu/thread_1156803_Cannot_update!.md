---
title: "Cannot update!"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by Arphitz on 2009-05-12
Hello guys,
Im total newb hear...
please help me...
currently im using ver 9.04 (jaunty)

the problem suddenly came out when in terminal I type "apt-get update"

the error msg is this....



'E:Type '--2009-05-12' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.'



also when i click synaptic package manager their show error message also, the message like this...



"E: Type  '--2009-05-12' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read/
Go to repository dialog to correct the problem.
E:  _cache->open() failed, please report.



:confused: im totally handicap now...please help

:((

---

### Post by Elfy on 2009-05-12
Remove the exisiting file 

```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```

Then redo the repository install
```
sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Should be fine now

---

### Post by Temposs on 2009-05-12
I think your error just means that the medibuntu servers are currently down. They go down occasionally, so just try again in a day and it should be fine.

In any case, you should be getting everything except medibuntu stuff, and it should update you if there's anything to update, except from medibuntu.

---

### Post by Elfy on 2009-05-12
> I think your error just means that the medibuntu servers are currently down. No the error means that there is something wrong with the medibuntu list - it seems to happen a fair bit.

You can edit the file, but it's easier in this case to remove it and start again imho.

I wouldn't do the same with the /etc/apt/sources.list however.

---

### Post by Arphitz on 2009-05-12
yeah!!!


thanks forestpixie!!!
now my machine is superb condition!
the case is already solve!


;)


thanks a lot!

---

