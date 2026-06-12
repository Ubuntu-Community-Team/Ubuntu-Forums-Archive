---
title: "Joining MP3 files"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by meddyliol on 2009-03-21
Hi, are there any programmes out there that will join MP3 files together? I have just purchased a talking book and would like to join the files together to put on my IPod.

Thanks

Brian :guitar:

---

### Post by taurus on 2009-03-21
Perhaps give audacity a try.

---

### Post by meddyliol on 2009-03-21
I will have a look at Audacity and see if it will do the job.

Thanks

Brian

---

### Post by MrWES on 2009-03-21
> **meddyliol said:**
> Hi, are there any programmes out there that will join MP3 files together? I have just purchased a talking book and would like to join the files together to put on my IPod.

Thanks

Brian :guitar:

cat file1.mp3 file2.mp3 > newfile.mp3

or

cat *.mp3 > newfile.mp3

Bill

---

### Post by meddyliol on 2009-03-21
Sorry for being so thick but what exactly do you mean by 'cat file1.mp3 file2.mp3 > newfile.mp3'.I have stored the MP3 files in the Music folder but how do I utilise your instructions?

PS Thanks for your help by the way

Brian

---

### Post by MrWES on 2009-03-21
> **meddyliol said:**
> Sorry for being so thick but what exactly do you mean by 'cat file1.mp3 file2.mp3 > newfile.mp3'.I have stored the MP3 files in the Music folder but how do I utilise your instructions?

PS Thanks for your help by the way

Brian

Open a terminal -- Applications | Accessories | Terminal

cd /path/to/your/mp3/files

cat *.mp3 > mybook.mp3

that will combine all your individual mp3 files into a new one called mybook.mp3

Bill

---

### Post by meddyliol on 2009-03-21
OK, thanks a lot for that.

Brian :popcorn:

---

### Post by Bölvaður on 2009-03-21
> **MrWES said:**
> Open a terminal -- Applications | Accessories | Terminal

cd /path/to/your/mp3/files

cat *.mp3 > mybook.mp3

that will combine all your individual mp3 files into a new one called mybook.mp3

Bill

here is an example of how I did it:

I had 3 test files on my Desktop (~/Desktop)

so I opened the terminal (as stated how to do above)

$ cd Desktop
$ cat *.mp3 > joined.mp3

I was surprised that concatting mp3 files would work but apparently the format is so that it does work (well at least in my test with those files I used).

---

### Post by MrWES on 2009-03-21
> **Bölvaður said:**
> here is an example of how I did it:

I had 3 test files on my Desktop (~/Desktop)

so I opened the terminal (as stated how to do above)

$ cd Desktop
$ cat *.mp3 > joined.mp3

I was surprised that concatting mp3 files would work but apparently the format is so that it does work (well at least in my test with those files I used).

Nod -- gotta love the power of the command line :).

avimerge and avisplit are nice too.

Bill

---

### Post by meddyliol on 2009-03-21
I am having a problem changing directory. My music is in the Home Folder/Music/POE/POE 1. When I put the following into the terminal cd/Home Folder/POE/POE 1  I get the following error message: bash: cd/Home: No such file or directory. What am I doing wrong?

Cheers

Brian :(

---

### Post by SuperSonic4 on 2009-03-21
```
cd /home/POE/POE\ 1
```

you can also use tab completion to get there

---

### Post by oldos2er on 2009-03-21
If your username is POE, run
```
cd "/home/POE/POE 1"
```
Because of the space in the name POE 1, you need to enclose it in quotes so the filesystem will recognize it.

---

### Post by MrWES on 2009-03-21
> **meddyliol said:**
> I am having a problem changing directory. My music is in the Home Folder/Music/POE/POE 1. When I put the following into the terminal cd/Home Folder/POE/POE 1  I get the following error message: bash: cd/Home: No such file or directory. What am I doing wrong?

Cheers

Brian :(

Brian,
Terminal commands have a space after the command; example cd_ /home/bill (underscore = space)
Also, when navigating in the terminal you can always use the tab key for autocompletion.

cd /home/b   <--- after the b key I can hit the tab key and the bash terminal will fill in the ill. Takes some getting use to, but very valuable once you master it. Also, if you have spaces in your directory names you can either put the path in quotes or use the \ to let the bash shell know a space follows.

Example. I have a folder in my home called My Documents, so it would look like this:

cd /home/bill/My\ Documents

Hope that helps. Learning some command line functions is valuable.

There are lots of resources on line to help you learn, here's one:
[http://www.linuxcommand.org/learning_the_shell.php]("http://www.linuxcommand.org/learning_the_shell.php")

Bill

---

