---
title: "Make words into binary"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by rasmukri on 2009-06-05
ok so maybe i am a noob but i know some stuff just not enough for cool things like this.
i was going through the forum and i found this you know you are a geek when... thread and a post saying how to convert words to binary and vice versa. but it doesn't make too much sense to me (sorry i hate noob questions) can anyone please explain how this is supposed to work? here is what it said:


> **infoburner said:**
> it heres the source code:
```

def dec2bin(n)
  [n].pack("N").unpack("B32")[0].sub(/^0+(?=\d)/, '')
end

def str2bin(str)
  str = str.split('').map{|c|c[0]}.map{|i| dec2bin(i)}
  str.map{|chr| chr.insert(0, "0") until chr.size == 8}
  str.join(" ")
end

def bin2str(str)
  str = str.split(" ")
  str.map{|i| eval("0b" + i)}.map{|i| i.chr}.join('')
end

```

so, do this: install irb via ```
sudo apt-get install irb
```
then cd to the directory you saved this file in and type ```
irb
```
then type 
```

require 'whateverfilenameyougaveit'
str2bin("your message goes here")

```
and it will spit your binary out, then
```

bin2str("10010101 010100101 010010110") # copy and paste this from the forum

```
and it will tell you what the binary says!
note that this 2 minute hack requires that the binary you paste into it be padded out to 8 digits for each character, and that each character is spereated by spaces.

01101000 01100001 01110110 01100101 00100000 01100110 01110101 01101110 00100001

---

### Post by Hospadar on 2009-06-05
Looks like python probably?
You can paste the code into a text file and then run it in python.

Would probably be best to learn python first though.

---

### Post by dcraven on 2009-06-05
It's Ruby.

---

### Post by KIAaze on 2009-06-05
Yep, and the instructions are very clear.
What exactly is your problem?

Note: You shouldn't give the file a .ruby extension. This gave me some problems.
"~" is also not recognized. Either use the full path to the file or cd to the directory.

Note2:
Hit ctrl+D to leave the irb session.

example session:
```

[1][~]$  cd Documents/
[2][~/Documents]$  ls ./geekdecoder.rb
./geekdecoder.rb
[3][~/Documents]$  irb
irb(main):001:0> require 'geekdecoder.rb'
=> true
irb(main):002:0> str2bin("Hello world!")
=> "01001000 01100101 01101100 01101100 01101111 00100000 01110111 01101111 01110010 01101100 01100100 00100001"
irb(main):003:0> bin2str("01001000 01100101 01101100 01101100 01101111 00100000 01110111 01101111 01110010 01101100 01100100 00100001")
=> "Hello world!"
irb(main):004:0> [4][~/Documents]$
[4][~/Documents]$  cat ./geekdecoder.rb
def dec2bin(n)
  [n].pack("N").unpack("B32")[0].sub(/^0+(?=\d)/, '')
end

def str2bin(str)
  str = str.split('').map{|c|c[0]}.map{|i| dec2bin(i)}
  str.map{|chr| chr.insert(0, "0") until chr.size == 8}
  str.join(" ")
end

def bin2str(str)
  str = str.split(" ")
  str.map{|i| eval("0b" + i)}.map{|i| i.chr}.join('')
end
[5][~/Documents]$

```

Just because I was curious, here's the thread  [You know you're a geek when........]("http://ubuntuforums.org/showthread.php?t=86237")

```
01001000 01100001 01110110 01100101 00100000 01100110 01110101 01101110 00101110 00100000 00111010 00101001 00100000 01000001 01101110 01100100 00100000 01101001 01100110 00100000 01111001 01101111 01110101 00100000 01101101 01100001 01101110 01100001 01100111 01100101 00100000 01110100 01101111 00100000 01100100 01100101 01100011 01101111 01100100 01100101 00100000 01110100 01101000 01101001 01110011 00111010 00100000 01101000 01110100 01110100 01110000 00111010 00101111 00101111 01101001 01110100 00101110 01110011 01101100 01100001 01110011 01101000 01100100 01101111 01110100 00101110 01101111 01110010 01100111 00101111 01100011 01101111 01101101 01101101 01100101 01101110 01110100 01110011 00101110 01110000 01101100 00111111 01110011 01101001 01100100 00111101 00110001 00110010 00110100 00110011 00110111 00111001 00110111 00100110 01100011 01101001 01100100 00111101 00110010 00111000 00110000 00110111 00110110 00110000 00110110 00110101 00100000 00101100 00100000 01110000 01101100 01100101 01100001 01110011 01100101 00100000 01110100 01100101 01101100 01101100 00100000 01101101 01100101 00100001 00100000 00111010 01000100

```
:)

---

### Post by QIII on 2009-06-05
They forgot:

When you really, honestly, dream in code.

---

### Post by rasmukri on 2009-06-06
ok well on to learning python then i guess because it makes no sense to me and that is prob why.

---

### Post by rasmukri on 2009-06-06
01010111 01100001 01101000 01101111 01101111 00100000 01101001 01110100 00100000 01110111 01101111 01110010 01101011 01110011

i guess i just needed a push in the right direction thanks.
i do have a question though when i named the file binary.py i could not get it to work. and i noticed on KIAaze's post it was labeled as a .rb file so i tried this and it works fine. so what is a .rb file?

---

### Post by kalesh7 on 2009-06-06
um a .rb file is a ruby file as a .py file is a python file

---

### Post by KIAaze on 2009-06-06
.rb is for Ruby files.
It's not Python, it's Ruby: [http://www.ruby-lang.org/en/](http://www.ruby-lang.org/en/) :)

Here's an interactive tutorial for it:
[http://tryruby.hobix.com/](http://tryruby.hobix.com/)

Of course, you could also learn Python, Perl, Tcl or any other programming language you want.

I think Python is more popular than Ruby. In any case, it's a good programming language for beginners. But Ruby looks nice too.

---

