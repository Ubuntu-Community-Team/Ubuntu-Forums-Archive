---
title: "basic bash script question"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by donkyhotay on 2010-02-18
I'm writing a script to help me automate packaging/distribution of a FOSS game I'm writing. I just wanted to confirm that:
```

read version
tar -czvf ./gamename_$version.tar.gz ./gamedir

```
is the proper way to add a variable into the middle of a string or if I need to do something else. Basically I want it to ask me for the version# which I just type in and then I can drop this into the remaining lines so that all the packages that are created automatically have the version of the game I'm packaging. So theoretically in the example above if I type

0.7.32

I get a package automatically named

gamename_0.7.32.tar.gz

I've seen examples online that show 
```

read name
tar -czvf ./$name.tar.gz ./gamedir

```
however I'm not certain if tossing the variable into the middle of the name will work or not and I'm away from my ubuntu system for awhile so I can't just test to find out myself.

---

### Post by HarrisonNapper on 2010-02-18
That should work just fine as that will set user input to the variable version. If it doesn't work, you can use
```
VERSION=$(read VERSION)
tar -czvf ./gamename_$VERSION.tar.gz ./gamedir
```

---

### Post by donkyhotay on 2010-02-18
Thanks, thats what I needed to know.

---

