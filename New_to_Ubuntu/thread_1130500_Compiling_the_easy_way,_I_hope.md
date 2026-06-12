---
title: "Compiling the easy way, I hope"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by h4mx0r on 2009-04-19
I'm sure there is probably some long winded guide on this with a lot of info but there are so many different methods of accomplishing a compile. I know when you use the install cd or what have you to get ubuntu on the machine they usually leave out a lot of developmental packages and compilers to trim down the fat for those that have less install room or a separate machine they do all the cross compiling on.

Is there a way to grab all the compile stuff? Some one fix line like apt-get install build-essential *-dev perhaps? Please any advice on recent screw ups people have had when trying to custom compile their own apps would be helpful. I know there is also cmake that is sometime used and module-assistant. What about compilers? Difference between mawk and gawk?

The reason I'm doing this is I have an app I'm going to use with many various config files and I'd like to stay up to date with its changelog watching out for changes in the code.

---

### Post by ibuclaw on 2009-04-19
If you are compiling a newer version of a package that is already in the repos, ensure to check the 'source code' box in '**System->Administration->Software Sources**' and type in
```
sudo apt-get build-dep *packagename*
```

Else, be sure to read the INSTALL or README text files that come with the tarballs, they should provide a list of all library dependencies, to which you search for the packagename**-dev** package and install those as needed.

To make the package:
```
./configure && make
```
To install:
```
sudo make install
```

Although some people swear to using tools such as **checkinstall** to make a pseudo-automated debian format package to allow uninstalling the software through any conventional package manager.

Regards
Iain

---

### Post by oldos2er on 2009-04-19
```
sudo apt-get install build-essential
```
will give you gcc.

---

