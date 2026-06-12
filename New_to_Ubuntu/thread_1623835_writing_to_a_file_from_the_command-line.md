---
title: "writing to a file from the command-line"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by olddai on 2010-11-17
I have created a file called myfile.txt. So could someone tell me how to write something into the file from the command-line please

---

### Post by Verbeck on 2010-11-17
> **olddai said:**
> I have created a file called myfile.txt. So could someone tell me how to write something into the file from the command-line please
vi /path/to/myfile.txt

---

### Post by viralmeme on 2010-11-17
> **olddai said:**
> I have created a file called myfile.txt. So could someone tell me how to write something into the file from the command-line please

$cat some text > myfile.txt

$ cat some text >> myfile.txt .. append to file

---

### Post by ironic.demise on 2010-11-17
> **viralmeme said:**
> $cat some text > myfile.txt
 
$ cat some text >> myfile.txt .. append to file
echo "some text">>myfile.txt
cat "some***file.txt***>>myfile.txt"
 
If you use only a single more than symbol *>*, it will delete the file and write ONLY what you asked it to. a double *>>* adds it onto the end without deleting anything.
 
cat is for files (It reads the file and outputs it, i.e. cat file.txt gives back the contents of file.txt)
Echo is for plain text.

---

### Post by realzippy on 2010-11-17
[http://lowfatlinux.com/linux-editor-vi.html](http://lowfatlinux.com/linux-editor-vi.html)
.....some *vi* basics.

---

### Post by olddai on 2010-11-17
Shows just how much of a noob i am. So i shall start from the beginning.

I created a text file called myfile.txt by using: touch myfile.txt
I also created a directory by using: mkdir Mytext
I moved myfile.txt into the Mytext directory by using: mv myfile.txt ~/Mytext
I typed ls to make sure that myfile was inside the Mytext directory

Now while i was still in the Mytext directory i typed:
cat "Up hill and over dale">>myfile.txt (clicked on Enter)

And was rewarded with: No such file or diectory

Would someone please tell me where i am going wrong?

---

### Post by olddai on 2010-11-17
Done it!

I used: echo "Up hill and over dale">>myfile.txt (clicked on enter)
and the used: cat myfile.txt to view the contents

Thanks for the replies everyone

---

### Post by nothingspecial on 2010-11-17
Try

```
echo "Up hill and over dale">>myfile.txt
cat myfile.txt
```

Also, I would recommend nano rather than vi for editing.

---

### Post by olddai on 2010-11-17
Shall have to remember those code tags lol. Thank nothingspecial

---

### Post by sisco311 on 2010-11-17
If you have to write more than a line to the file, use the here document redirection:
```
cat << EOF >> filename
line 1
line 2
...
EOF
```

See:
```
man bash | less +/"Here Documents"
```

---

### Post by Hippytaff on 2010-11-17
> **nothingspecial said:**
> Try
 
```
echo "Up hill and over dale">>myfile.txt
cat myfile.txt
```
 
Also, I would recommend nano rather than vi for editing.
 
I alos much prefer Nano to Vi - Vi is hard for us noobs :-)

---

