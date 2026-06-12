---
title: "Runnint MatLab from terminal"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by bzm3r on 2009-05-31
I just installed MatLab for UNIX from my installation disk, but I have a minor problem. I am unable to run MatLab from terminal.

I tried changing directories in terminal right to the folder that contains an 'executable text file' called matlab (which is what I have been double clicking on to use MatLab), and then typing in *matlab* in terminal, but nothing happens.

What should I do to be able to run matlab directly from terminal?

---

### Post by ad_267 on 2009-05-31
Change into the directory where the matlab executable is and type "./matlab"

To make it so you don't have to do this, create a symbolic link to the matlab executable from somewhere in your path. Eg:

```
sudo ln -s /path/to/matlab /usr/local/bin/matlab
```

Then you can run matlab from anywhere with "matlab".

---

