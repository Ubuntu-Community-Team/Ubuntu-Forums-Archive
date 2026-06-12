---
title: "BASH - Output to multiple lines of file"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by linuxguymarshall on 2009-07-10
I am writing a script that generates a custom configuration file that takes input and depending on what they choose it will edit the configuration file correctly. Basically the code does this
```

echo "Would you like x to be y?"
read foo
if [ $foo = yes ]
then
foo=t
read x
elif [ $x = no ]
then
foo=f
else
echo "not an option"
fi
```

and this happpens a few times with different questions and different variables. 

The end result is a single file that reads like this

```

FOO=$foo
BAR=$bar

```

But I can't find a way to output to a file on multiple lines.    Any suggestions?

---

### Post by linuxguymarshall on 2009-07-10
Ok, I have figured out how to do it. I have to create a function and tell that function to output to the file. Like this. 

```

conf(){
echo "$foo"
echo "$bar"
}
echo "Would you like x to be y?"
read foo
if [ $foo = yes ]
then
foo=t
read x
elif [ $x = no ]
then
foo=f
else
echo "not an option"
fi
conf >> file.conf

```

---

