---
title: "How to split a text file into many text files by a splitting string..."
date: 2009-10-16
forum: New to Ubuntu
---

### Post by Guruprasad on 2009-10-16
I have a text file like

Line 1 matter
Line 2 matter
Line 3 matter
Splitting Text
Line 5 matter
Line 6 matter
Line 7 matter
Line 8 matter
Line 9 matter
Splitting Text
Line 11 matter
Line 12 matter
Line 13 matter
Line 14 matter


I want to split them into smaller file with splitting text like this

File 1
Line 1 matter
Line 2 matter
Line 3 matter


File 2
Line 5 matter
Line 6 matter
Line 7 matter
Line 8 matter
Line 9 matter


File 3
Line 11 matter
Line 12 matter
Line 13 matter
Line 14 matter

---

### Post by benj1 on 2009-10-16
```
#! /usr/bin/env python
files = open('foobar.txt','r').read().split('Splitting Text')
names=['file1','file2','file3']
for num,file in enumerate(files):
    open(names[num],'w').write(file)

```

should do it

---

### Post by lavinog on 2009-10-16
```

#! /usr/bin/env python

inputfile = 'test.txt'
splittingtxt = 'Splitting Text'
filenameformat = 'file#.txt'

def newfout(filenum):
    filename = filenameformat.replace('#',str(filenum) )
    fout=open(filename,'w')
    return fout


file = open( inputfile )
lines=file.readlines()
    
filenum=1
fout = newfout(filenum)

for line in lines:
    if splittingtxt in line:
        fout.close()
        filenum+=1
        fout = newfout( filenum )
    else:
        fout.write(line)
        
fout.close()

```

---

### Post by benj1 on 2009-10-16
mines shorter :P

---

### Post by lavinog on 2009-10-16
> **benj1 said:**
> mines shorter :P

mine doesn't assume that there will only be three files

---

### Post by kaibob on 2009-10-16
You can use the csplit utility. For example,

```
csplit file '/Splitting Text/' '{*}'
```

See the man page for options.

---

### Post by lavinog on 2009-10-16
revised to be shorter:
```

#! /usr/bin/env python

inputfile = 'test.txt'
splittingtxt = 'Splitting Text'
filenameformat = 'file#.txt'

def output(filenum,line):
    filename = filenameformat.replace('#',str(filenum) )
    fout=open(filename,'w')
    fout.write(line)
    fout.close

file = open( inputfile )
lines=file.read().split(splittingtxt)

for i in range(0,len( lines ) ):
    output( i+1 , lines[i] )

```

csplit is likely to be what the op wants

---

### Post by benj1 on 2009-10-16
fine :)
```

#! /usr/bin/env python
files = open('foobar.txt','r').read().split('Splitting Text')
names = ['file'+ str(num) for num in range(len(files))]
for num,file in enumerate(files):
    open(names[num],'w').write(file)

```

---

### Post by iponeverything on 2009-10-16
> **kaibob said:**
> You can use the csplit utility. For example,

```
csplit file '/Splitting Text/' '{*}'
```

See the man page for options.

Have to say, flipping csplit out of the swiss army knife was a cool trick.

---

