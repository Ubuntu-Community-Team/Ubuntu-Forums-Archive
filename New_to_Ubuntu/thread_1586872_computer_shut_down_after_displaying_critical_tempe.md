---
title: "computer shut down after displaying critical temperature reaches..."
date: 2010-10-02
forum: New to Ubuntu
---

### Post by twaher on 2010-10-02
hi everyone ..I encounter a problem while installing ubuntu inside windows..the installation is properly done and the computer is restarted. i select ubuntu to continue with the installation process but unfortunately it displays "critical temperature reached....." and it shuts down after the pink color background appear. can anyone help please..thanks

---

### Post by coffeecat on 2010-10-02
> **twaher said:**
> "critical temperature reached....."

I guess this would be the BIOS sending a shutdown message to Windows because your CPU (or something) is in danger of overheating. I'm surprised that the CPU would get that overloaded with a simple Ubuntu installation. You need to look at your hardware and ventilation.

Is this a desktop or laptop? If a desktop you need to look inside the case. Is there a buildup of dust and fluff on the vents preventing proper ventilation? Is the CPU cooler adequate? Is the fan on it working? 

If laptop, are you keeping the ventilation ports clear of obstruction? Is there a buildup of dust/fluff?

---

### Post by twaher on 2010-10-03
hi.its a desktop pc..i thought about the same problem concerning the airflow. i opened and removed a huge amount of dust on the fan found on the CPU..but unfortunately same things happen..

_computer information_
motherboard: abit
CPU: core 2 duo 2.4
Memory: 1Gb
hard disk: 160

---

### Post by sikander3786 on 2010-10-03
Can you remove the heat sink? If yes, remove it and again try to clean it with compressed air and also put some cooling paste between processor and the heat sink.

---

### Post by coffeecat on 2010-10-03
> **twaher said:**
> hi.its a desktop pc..i thought about the same problem concerning the airflow. i opened and removed a huge amount of dust on the fan found on the CPU..but unfortunately same things happen..

Did you check whether the fan is actually spinning? Make sure the power cable to the fan has not become unseated from the motherboard connector.

If you've used the machine enough for the fan to collect a huge amount of dust, the fan itself might be failing. Was it a quality CPU cooler that you fitted yourself, or a generic one that comes with OEM computers?

---

### Post by twaher on 2010-10-03
thanks a lot for you help..i really appreciate..the problem is that there was no silicon between the cpu and the fan. the cpu was heated up to 121 degrees..

---

### Post by JustinR on 2010-10-03
> **twaher said:**
> thanks a lot for you help..i really appreciate..the problem is that there was no silicon between the cpu and the fan. the cpu was heated up to 121 degrees..

Was that Fahrenheit or Celsius?

---

### Post by amjjawad on 2010-10-03
In my BIOS, there are some settings for the temperature. Even there are some settings for the CPU's Fan. It's good idea to have a look at these settings.

Sometimes, it would be good idea to open the case and leave it open until you make sure everything is ok.

I don't think installing Ubuntu caused the problem.

---

### Post by coffeecat on 2010-10-03
> **twaher said:**
> the problem is that there was no silicon between the cpu and the fan.

No thermal compound. That would explain it. I think you mean none between the CPU and the heatsink, but I understand. 

Have you applied thermal compound before? Do you know what to do? Do you want any help?

---

### Post by twaher on 2010-10-09
thank you very much for all your help..i finally succeed in repairing it..am sorry i have taken lots of time to reply back..i have added the silicon between the cpu and the heatsink..this solve the issue..there was silicon before but due to heat it has melted..

---

### Post by amjjawad on 2010-10-09
> **twaher said:**
> thank you very much for all your help..i finally succeed in repairing it..am sorry i have taken lots of time to reply back..i have added the silicon between the cpu and the heatsink..this solve the issue..there was silicon before but due to heat it has melted..

Congratulation :)

Don't forget to mark this thread as "SOLVED" please :)

---

