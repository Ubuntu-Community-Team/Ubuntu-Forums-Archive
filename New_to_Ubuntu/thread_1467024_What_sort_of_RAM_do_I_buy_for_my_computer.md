---
title: "What sort of RAM do I buy for my computer"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by hanzj on 2010-04-30
I'm a big newbie and am considering getting another 1 GB stick of RAM.


What type do I need? What will work/fit with my computer? How do I find the answers? IS there a command line command I can do to see what my RAM hardware is?

---

### Post by MrWES on 2010-04-30
Try here:

[http://www.crucial.com/]("http://www.crucial.com/")

---

### Post by hanzj on 2010-04-30
mrwes,
the 1st question on the crucial site:
Manufacturer.

How do i know my  manufacturer? (It's not a big-name brand). 

And manufacturer of what?... the whole comp? or just the motherboard?

---

### Post by MrWES on 2010-04-30
The PC/laptop brutha!

---

### Post by Teber on 2010-04-30
the manufacturer of the ram chip

---

### Post by hanzj on 2010-04-30
mrwes,
it's got no name on the outside. so i don't know the manufacturer.

i think this was a customized computer.

---

### Post by hanzj on 2010-04-30
teber says ram chip maker. mrwes says entire computer maker.

---

### Post by Teber on 2010-04-30
ram chip maker. computer assembler. hp and dell assemble third party components

---

### Post by hanzj on 2010-04-30
ok. how do i know the ram chip maker name via command line?

or do i have to open up the computer case?

---

### Post by Teber on 2010-04-30
i would open the case. and take the mounted ram chip with me to the computer shop. as to purchase exactly the same type of ram chip. it's best to have a matching set.

actually that's what i did when upgrading my ram

custom built computers are assembled from the same parts as factory built ones.

---

### Post by MrWES on 2010-04-30
$ sudo dmidecode --type 17 | more

---

### Post by hanzj on 2010-04-30
here's what i get from
> sudo dmidecode --type 17 | more
> Handle 0x001F, DMI type 17, 21 bytes
Memory Device
    Array Handle: 0x001E
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: A0
    Bank Locator: Bank0/1
    Type: Unknown
    Type Detail: None

Handle 0x0020, DMI type 17, 21 bytes
Memory Device
    Array Handle: 0x001E
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: A1
    Bank Locator: Bank2/3
    Type: Unknown
    Type Detail: None

Handle 0x0021, DMI type 17, 21 bytes
Memory Device
    Array Handle: 0x001E
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 512 MB
    Form Factor: DIMM
    Set: None
    Locator: A2
    Bank Locator: Bank4/5
    Type: Unknown
    Type Detail: None

Handle 0x0022, DMI type 17, 21 bytes
Memory Device
    Array Handle: 0x001E
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 512 MB
    Form Factor: DIMM
    Set: None
    Locator: A3
    Bank Locator: Bank6/7
    Type: Unknown
    Type Detail: None



---

### Post by walt.smith1960 on 2010-04-30
Do we assume that you don't have a book for the motherboard? If not, I don't know any choice but to open the case and try to find the motherboard manufacturer & model number. Once you have those, you can go to the manufacturer's web site and find information including RAM type.  You should also be able to download the motherboard manual. Use a little patience and not too much force and opening a PC case is not that hard.

---

### Post by JKyleOKC on 2010-04-30
try "subo lshw|less" to get a comprehensive listing of all your hardware; however taking one of the existing sticks along when you go to the store is still a good idea!

---

### Post by Deja_Who2 on 2010-04-30
It would help to know what processor you have and a little better description of your memory module.

However, it appears that you currently have two 512MB modules totaling 1GB.  It looks like you have two open slots which you could add another two 512MB modules bringing your total up to 2GB.

My best guess for what you have is: (2) 512MB, 168-pin DIMM, SDRAM, PC133 memory modules.

I like crucial.com, you can find this module under the part number CT64M64S4D75 there.  They have good pictures and more info which you can compare to your existing memory when you finally crack open the case.

I hope this helps!

---

