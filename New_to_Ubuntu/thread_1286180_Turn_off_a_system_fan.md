---
title: "Turn off a system fan?"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by Remagen on 2009-10-08
Well, I built a computer the other day, but I've got one problem.

There are 3 fans on the case and 1 CPU fan.  All the fans are running all the time, at max speed, this is really annoying. 

I've been searching all over for a way to manage the fans, but lm-sensors doesn't seem to have any drivers that support my hardware yet.

I only use Ubuntu for work and internet browsing, so I figure I can get away with just turning off one of the system fans altogether, how would I go about doing this?

I'll post my mobo info/sensors-detect output:

```
Now follows a summary of the probes I have just done.
Just press ENTER to continue:  

Driver `to-be-written' (should be inserted):
  Detects correctly:
  * Bus `NVIDIA i2c adapter '
    Busdriver `UNKNOWN', I2C address 0x2e
    Chip `Analog Devices ADT7473' (confidence: 5)
  * Chip `AMD K10 thermal sensors' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# Chip drivers
# no driver for Analog Devices ADT7473 yet
#----cut here----

```

I should note that gkrell can read my GPU and hardrive temps, as well as my fan speeds.  So, I would figure that actually controlling my fans based on GPU would be possible.

---

### Post by Tamlynmac on 2009-10-08
Why not just unplug one of the case fans. If you find you don't need it, it will become a reserve case fan for when one of the other case fans fail (which they will eventually). You may even place a switch in series with the fan and be able to turn it on and off on the back of the case. That way you don't rely on software to control the fan. Correct me if I'm wrong but it's probably only a two wire fan.

Just a thought.

---

### Post by Remagen on 2009-10-08
I'm duel booting this with windows, which I game on, so I can't really unplug the fan.

However, I did turn on 'Cool n' Quiet' in BIOS, and the fans have quieted down to reasonable levels.  

But I don't know if the fans will ramp up when I put stress on the processor anyone have a good idea to stress test?

---

### Post by wojox on 2009-10-08
Load Windows :P



And play a game. Do they run constantly in that environment?

---

### Post by Zoot7 on 2009-10-08
> **Remagen said:**
> I'm duel booting this with windows, which I game on, so I can't really unplug the fan.

However, I did turn on 'Cool n' Quiet' in BIOS, and the fans have quieted down to reasonable levels.  

But I don't know if the fans will ramp up when I put stress on the processor anyone have a good idea to stress test?
You could look into getting a fan controller, they're not that dear anymore.

Just a suggestion. :)

---

### Post by Remagen on 2009-10-08
Well, using a later version of lm-sensors, I managed to get some output:
```
@dormix:/tmp$ sudo sensors
it8720-isa-0290
Adapter: ISA adapter
in0:         +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in1:         +1.62 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +1.15 V  (min =  +0.00 V, max =  +4.08 V)   
in3:         +2.93 V  (min =  +0.00 V, max =  +4.08 V)   
in4:         +4.08 V  (min =  +0.00 V, max =  +3.06 V)   ALARM
in5:         +4.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in6:         +4.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in7:         +4.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in8:         +3.36 V
fan1:       3040 RPM  (min =    0 RPM)
fan2:        537 RPM  (min =    0 RPM)
fan3:        912 RPM  (min =    0 RPM)
temp1:       +33.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermistor
temp2:       +45.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermistor
temp3:      -128.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = disabled
cpu0_vid:   +1.550 V

```

But it seems to be missing a specific CPU temp (any ideas about temp1 & 2?)

---

### Post by Cresho on 2009-10-08
case fan is an artform...really!

I was looking around for something to control the speed of my fans sinc years.  Recently, i took a look at bay fan controllers which most of them fail 99% of the time in achieving my goal.  Then... suddenly i found these


[http://www.newegg.com/Product/Product.aspx?Item=N82E16835999111](http://www.newegg.com/Product/Product.aspx?Item=N82E16835999111)


These fans have thermal sensors built in!  you mount the fan to the case, and the sensor to the object you want your fan to cool.

In my case, I have 2 fans in the front with sensors on the harddrives.  I have removed the powerbox fan and replaced the big 120mm and put the sensor on the powercase itself.  I put a system back fan and placed the sensor on the chases.  It is dead quiet unless i render video.  when my case gets hot, the fans kick in at the speed auto required and it cools it down fast.  these fans have high desible range but you wont notice it since they work really well and the pc is very quiet.  Since i managed to optimize fan placement and sensor placement, the pc is very quiet.

---

