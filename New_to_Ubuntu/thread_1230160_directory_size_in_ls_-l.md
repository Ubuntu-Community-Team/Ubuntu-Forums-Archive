---
title: "directory size in ls -l"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by bilol on 2009-08-03
Hi all,
```
dhiman@dhiman-desktop:~$ ls -ls
total 6952
   8 -rwxr-xr-x 1 dhiman dhiman    7797 2009-06-17 13:49 a.out
   4 -rw-r--r-- 1 dhiman dhiman     378 2009-06-19 17:43 cin.sh
   4 drwxr-xr-x 2 dhiman dhiman    4096 2009-07-31 17:20 Desktop
 108 -rw-r--r-- 1 dhiman dhiman  104604 2009-07-10 13:58 dkTestPrint.pdf
   4 drwxr-xr-x 2 dhiman dhiman    4096 2009-07-30 16:41 Documents
  80 drwxr-xr-x 2 dhiman dhiman   77824 2009-07-13 12:38 dpkg-repack130709
   0 lrwxrwxrwx 1 dhiman dhiman      26 2009-05-07 18:50 Examples -> /usr/share/example-content
   4 -rw-r--r-- 1 dhiman dhiman      66 2009-05-11 17:02 hello.c
   4 drwxr-xr-x 2 dhiman dhiman    4096 2009-05-07 18:52 Music
   4 drwx------ 2 dhiman dhiman    4096 2009-07-30 12:15 MyDownloads
   4 -rw-r--r-- 1 dhiman dhiman      85 2009-07-31 15:49 myfl
   4 drwx------ 2 dhiman dhiman    4096 2009-07-31 17:21 OS
   4 drwxr-xr-x 2 dhiman dhiman    4096 2009-06-11 13:08 Photos
   4 drwxr-xr-x 4 dhiman dhiman    4096 2009-06-10 15:17 Pictures
   4 drwxr-xr-x 2 dhiman dhiman    4096 2009-05-07 19:03 Public
   4 drwxr-xr-x 3 dhiman dhiman    4096 2009-06-04 12:17 ramkrishna
   4 drwxr-xr-x 2 dhiman dhiman    4096 2009-05-07 19:03 Templates
   4 -rw-r--r-- 1 dhiman dhiman      14 2009-07-31 16:06 urfl
   4 drwxr-xr-x 2 dhiman dhiman    4096 2009-06-01 14:41 Videos
6696 -rw-r--r-- 1 dhiman dhiman 6841784 2009-07-27 20:26 wget-log

```

The 6th field signifies the byte count of the files.What does it signify for directories? 
Why is it 4096 for the directory Desktop and 77824 for the directory dpkg-repack130709?
Can't get exact information by googling.
Need your help....

---

### Post by colau on 2009-08-03
> **bilol said:**
> Hi all,
```
dhiman@dhiman-desktop:~$ ls -ls
total 6952
   8 -rwxr-xr-x 1 dhiman dhiman    7797 2009-06-17 13:49 a.out
   4 -rw-r--r-- 1 dhiman dhiman     378 2009-06-19 17:43 cin.sh
   4 drwxr-xr-x 2 dhiman dhiman    4096 2009-07-31 17:20 Desktop
 108 -rw-r--r-- 1 dhiman dhiman  104604 2009-07-10 13:58 dkTestPrint.pdf
   4 drwxr-xr-x 2 dhiman dhiman    4096 2009-07-30 16:41 Documents
  80 drwxr-xr-x 2 dhiman dhiman   77824 2009-07-13 12:38 dpkg-repack130709
   0 lrwxrwxrwx 1 dhiman dhiman      26 2009-05-07 18:50 Examples -> /usr/share/example-content
   4 -rw-r--r-- 1 dhiman dhiman      66 2009-05-11 17:02 hello.c
   4 drwxr-xr-x 2 dhiman dhiman    4096 2009-05-07 18:52 Music
   4 drwx------ 2 dhiman dhiman    4096 2009-07-30 12:15 MyDownloads
   4 -rw-r--r-- 1 dhiman dhiman      85 2009-07-31 15:49 myfl
   4 drwx------ 2 dhiman dhiman    4096 2009-07-31 17:21 OS
   4 drwxr-xr-x 2 dhiman dhiman    4096 2009-06-11 13:08 Photos
   4 drwxr-xr-x 4 dhiman dhiman    4096 2009-06-10 15:17 Pictures
   4 drwxr-xr-x 2 dhiman dhiman    4096 2009-05-07 19:03 Public
   4 drwxr-xr-x 3 dhiman dhiman    4096 2009-06-04 12:17 ramkrishna
   4 drwxr-xr-x 2 dhiman dhiman    4096 2009-05-07 19:03 Templates
   4 -rw-r--r-- 1 dhiman dhiman      14 2009-07-31 16:06 urfl
   4 drwxr-xr-x 2 dhiman dhiman    4096 2009-06-01 14:41 Videos
6696 -rw-r--r-- 1 dhiman dhiman 6841784 2009-07-27 20:26 wget-log

```

The 6th field signifies the byte count of the files.What does it signify for directories? 
Why is it 4096 for the directory Desktop and 77824 for the directory dpkg-repack130709?
Can't get exact information by googling.
Need your help....

Every directory is considered as file in linux.
Directories are of 4K bytes.
77824 is the size of dpkg-repack130709.
```

ls -lsh

```

---

### Post by colau on 2009-08-03
From 
```

man ls

```

```

-l     use a long listing format

-s, --size
       print the size of each file, in blocks

```

---

### Post by bilol on 2009-08-03
Hi,

> Every directory is considered as file in linux.
Directories are of 4K bytes.
77824 is the size of dpkg-repack130709.

My question is ...How 77824 is the size of dpkg-repack130709? What does 77824 signify?

---

### Post by colau on 2009-08-03
> **bilol said:**
> Hi,



My question is ...How 77824 is the size of dpkg-repack130709? What does 77824 signify?
Can you post the output of dpkg-repack130709 directory?
```

cd dpkg-repack130709
ls -lsh

```

---

### Post by bilol on 2009-08-03
Since the output is too large, I am giving it partially:

```
total 711M
  44K -rw-r--r-- 1 dhiman dhiman  43K 2009-07-13 12:14 acl_2.2.45-1_i386.deb
  12K -rw-r--r-- 1 dhiman dhiman  12K 2009-07-13 12:14 acpi_0.09-3ubuntu1_i386.deb
  32K -rw-r--r-- 1 dhiman dhiman  31K 2009-07-13 12:14 acpid_1.0.4-5ubuntu9.3_i386.deb
  48K -rw-r--r-- 1 dhiman dhiman  46K 2009-07-13 12:14 acpi-support_0.109-0hardy2_i386.deb
 132K -rw-r--r-- 1 dhiman dhiman 128K 2009-07-13 12:14 adduser_3.105ubuntu1_i386.deb

```

---

### Post by gali98 on 2009-08-03
Just a guess...
Maybe the directory had so many files in it, it needed more than 4096 bytes to store all the info it needed...
77824 / 4096 = 19 (as in perfect 19....)
hmmmm....
Kory

---

### Post by bilol on 2009-08-03
Thanks for all your suggestion and answers,but still I have doubts.
Let me give you the following output:
```
dhiman@dhiman-desktop:~$ ls -ls /media/EduDocu/EduDocu/
total 121
  0 drwxrwxrwx 1 root root      0 2009-05-14 15:21 codeDoc
  0 drwxrwxrwx 1 root root      0 2009-07-06 14:10 DKode
  4 drwxrwxrwx 1 root root   4096 2009-05-14 15:21 DKode_old
104 -rwxrwxrwx 1 root root 103712 2009-05-29 10:04 DKontacts.pdf
  0 drwxrwxrwx 1 root root      0 2009-07-06 14:24 Images
  0 drwxrwxrwx 1 root root      0 2009-05-14 15:26 ISI_PLP
  1 -rwxrwxrwx 2 root root    272 2009-07-01 15:13 libtest_out.txt
  4 -rwxrwxrwx 1 root root   1509 2009-06-17 13:48 linreg1.c
  0 drwxrwxrwx 1 root root      0 2009-05-14 15:38 linuxSetups
  0 drwxrwxrwx 1 root root      0 2009-07-01 14:17 Miscellaneous
  8 -rwxrwxrwx 1 root root   5564 2009-06-01 09:50 PCAultimate.m
  0 drwxrwxrwx 1 root root      0 2009-07-01 14:16 Topics
  0 drwxrwxrwx 1 root root      0 2009-05-14 15:13 UBUNTU
```

Can you explain why the 6th field of codeDoc is 0,DKode is 0 and DKode_old is 4096 by analyzing the following output:

```
dhiman@dhiman-desktop:~$ ls -ls /media/EduDocu/EduDocu/codeDoc
total 208
36 -rwxrwxrwx 1 root root 33792 2009-02-26 16:34 clc1.doc
36 -rwxrwxrwx 1 root root 36864 2009-02-18 12:57 clc.doc
28 -rwxrwxrwx 1 root root 26112 2009-02-19 16:37 firstPCPCA.doc
28 -rwxrwxrwx 1 root root 27648 2009-02-19 16:47 function PC.doc
44 -rwxrwxrwx 1 root root 44544 2009-03-23 15:24 function WX.doc
20 -rwxrwxrwx 1 root root 20480 2009-02-13 14:02 Hi.doc
16 -rwxrwxrwx 1 root root 15310 2009-02-18 13:59 PCA.rar

dhiman@dhiman-desktop:~$ ls -ls /media/EduDocu/EduDocu/DKode
total 0
0 drwxrwxrwx 1 root root 0 2009-07-06 14:10 C
0 drwxrwxrwx 1 root root 0 2009-07-06 17:16 MatLab

dhiman@dhiman-desktop:~$ ls -ls /media/EduDocu/EduDocu/DKode_old
total 7
4 -rwxrwxrwx 1 root root 679 2009-03-02 16:18 arr1.sh
1 -rwxrwxrwx 1 root root 596 2009-03-02 14:11 bubble.sh
0 drwxrwxrwx 1 root root   0 2009-05-14 15:21 c
1 -rwxrwxrwx 1 root root  66 2009-03-31 14:09 hi.c
0 drwxrwxrwx 1 root root   0 2009-05-14 15:20 html
0 drwxrwxrwx 1 root root   0 2009-05-14 15:21 java
1 -rwxrwxrwx 1 root root  59 2009-03-02 16:28 loop.sh
0 drwxrwxrwx 1 root root   0 2009-05-14 15:21 steganography
1 -rwxrwxrwx 1 root root  35 2008-12-15 13:45 test.c
1 -rwxrwxrwx 1 root root  79 2009-03-02 14:10 testing.sh


```
please help....

---

### Post by gali98 on 2009-08-04
> 
  **0** drwxrwxrwx 1 root root      0 2009-05-14 15:21 codeDoc
  **0** drwxrwxrwx 1 root root      0 2009-07-06 14:10 DKode
  **4** drwxrwxrwx 1 root root   4096 2009-05-14 15:21 DKode_old
I think this means something (though not exactly what). The directories that have 0 as the first number also have 0 under the size number.
Kory

---

### Post by niteshifter on 2009-08-04
Hi,

```
  0 drwxrwxrwx 1 root root      0 2009-05-14 15:21 codeDoc
                                ^                         
```

That field (marked with ^) really is the size in disk allocation units (1K, 2K 4K - depending upon the file system type and how it was configured).
Source - ls info file:
```
info coreutils 'ls invocation' 'What information is listed'
```
(man ls is a bit terse!)

As to why it's 0 in your example. I'm not sure, but I suspect that's a NTFS (or VFAT) file system drive you've got mounted on /media/EduDocu.

---

### Post by bilol on 2009-08-05
Hi all,
> but I suspect that's a NTFS (or VFAT) file system drive you've got mounted on /media/EduDocu.
Right, it is mounted on NTFS and I suppose,the default block size there is 512 bytes,as it may be  evident from the following output:
```
dhiman@dhiman-desktop:~$ ls -lsh /media/EduDocu/EduDocu/DKode_old
total 7.0K
4.0K -rwxrwxrwx 1 root root 679 2009-03-02 16:18 arr1.sh
1.0K -rwxrwxrwx 1 root root 596 2009-03-02 14:11 bubble.sh
   0 drwxrwxrwx 1 root root   0 2009-05-14 15:21 c
 512 -rwxrwxrwx 1 root root  66 2009-03-31 14:09 hi.c
   0 drwxrwxrwx 1 root root   0 2009-05-14 15:20 html
   0 drwxrwxrwx 1 root root   0 2009-05-14 15:21 java
 512 -rwxrwxrwx 1 root root  59 2009-03-02 16:28 loop.sh
   0 drwxrwxrwx 1 root root   0 2009-05-14 15:21 steganography
 512 -rwxrwxrwx 1 root root  35 2008-12-15 13:45 test.c
 512 -rwxrwxrwx 1 root root  79 2009-03-02 14:10 testing.sh

```
But the thing that I am really getting confused is the following:
```
dhiman@dhiman-desktop:~$ cd /media/EduDocu/EduDocu/
dhiman@dhiman-desktop:/media/EduDocu/EduDocu$ ls -lshd codeDoc DKode DKode_old 
   0 drwxrwxrwx 1 root root    0 2009-05-14 15:21 codeDoc
   0 drwxrwxrwx 1 root root    0 2009-07-06 14:10 DKode
4.0K drwxrwxrwx 1 root root 4.0K 2009-05-14 15:21 DKode_old

```
How can the size of the directory(codeDoc) be 0 ,though it is  non-empty.
For further assistance I am providing the following information:
```
dhiman@dhiman-desktop:/media/EduDocu/EduDocu$ ls -lsh codeDoc DKode DKode_old 
codeDoc:
total 208K
36K -rwxrwxrwx 1 root root 33K 2009-02-26 16:34 clc1.doc
36K -rwxrwxrwx 1 root root 36K 2009-02-18 12:57 clc.doc
28K -rwxrwxrwx 1 root root 26K 2009-02-19 16:37 firstPCPCA.doc
28K -rwxrwxrwx 1 root root 27K 2009-02-19 16:47 function PC.doc
44K -rwxrwxrwx 1 root root 44K 2009-03-23 15:24 function WX.doc
20K -rwxrwxrwx 1 root root 20K 2009-02-13 14:02 Hi.doc
16K -rwxrwxrwx 1 root root 15K 2009-02-18 13:59 PCA.rar

DKode:
total 0
0 drwxrwxrwx 1 root root 0 2009-07-06 14:10 C
0 drwxrwxrwx 1 root root 0 2009-07-06 17:16 MatLab

DKode_old:
total 7.0K
4.0K -rwxrwxrwx 1 root root 679 2009-03-02 16:18 arr1.sh
1.0K -rwxrwxrwx 1 root root 596 2009-03-02 14:11 bubble.sh
   0 drwxrwxrwx 1 root root   0 2009-05-14 15:21 c
 512 -rwxrwxrwx 1 root root  66 2009-03-31 14:09 hi.c
   0 drwxrwxrwx 1 root root   0 2009-05-14 15:20 html
   0 drwxrwxrwx 1 root root   0 2009-05-14 15:21 java
 512 -rwxrwxrwx 1 root root  59 2009-03-02 16:28 loop.sh
   0 drwxrwxrwx 1 root root   0 2009-05-14 15:21 steganography
 512 -rwxrwxrwx 1 root root  35 2008-12-15 13:45 test.c
 512 -rwxrwxrwx 1 root root  79 2009-03-02 14:10 testing.sh

```

Please clarify my doubts....

---

### Post by mikechant on 2009-08-05
I seem to remember that NTFS can store (very) small files in the 'spare space' of the directory entry of the directory that contains them. If the small files happen to also be directories, then those directories wouldn't need any space specifically allocated (even though files within them would).

In effect, I'm thinking that the (internal format equivalent) of this info:
```
codeDoc:
total 208K
36K -rwxrwxrwx 1 root root 33K 2009-02-26 16:34 clc1.doc
36K -rwxrwxrwx 1 root root 36K 2009-02-18 12:57 clc.doc
28K -rwxrwxrwx 1 root root 26K 2009-02-19 16:37 firstPCPCA.doc
28K -rwxrwxrwx 1 root root 27K 2009-02-19 16:47 function PC.doc
44K -rwxrwxrwx 1 root root 44K 2009-03-23 15:24 function WX.doc
20K -rwxrwxrwx 1 root root 20K 2009-02-13 14:02 Hi.doc
16K -rwxrwxrwx 1 root root 15K 2009-02-18 13:59 PCA.rar

DKode:
total 0
0 drwxrwxrwx 1 root root 0 2009-07-06 14:10 C
0 drwxrwxrwx 1 root root 0 2009-07-06 17:16 MatLab
```

Is packed into the directory entry for /media/EduDocu/EduDocu

But there's no room for this:
```
DKode_old:
total 7.0K
4.0K -rwxrwxrwx 1 root root 679 2009-03-02 16:18 arr1.sh
1.0K -rwxrwxrwx 1 root root 596 2009-03-02 14:11 bubble.sh
   0 drwxrwxrwx 1 root root   0 2009-05-14 15:21 c
 512 -rwxrwxrwx 1 root root  66 2009-03-31 14:09 hi.c
   0 drwxrwxrwx 1 root root   0 2009-05-14 15:20 html
   0 drwxrwxrwx 1 root root   0 2009-05-14 15:21 java
 512 -rwxrwxrwx 1 root root  59 2009-03-02 16:28 loop.sh
   0 drwxrwxrwx 1 root root   0 2009-05-14 15:21 steganography
 512 -rwxrwxrwx 1 root root  35 2008-12-15 13:45 test.c
 512 -rwxrwxrwx 1 root root  79 2009-03-02 14:10 testing.sh
```
So it is stored in a seperate 4k directory block.

---

