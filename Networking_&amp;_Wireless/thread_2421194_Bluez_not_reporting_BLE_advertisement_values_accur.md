---
title: "Bluez not reporting BLE advertisement values accurately via d-bus"
date: 2019-06-18
forum: Networking &amp; Wireless
---

### Post by kirang on 2019-06-18
I am trying to read temperature values from a BLE Temperature sensor (bluemaestro tempo disc)

I am developing in c++ using intel's tinyb library which interfaces with bluez via d-bus. This application parses the advertisement packet for the manufacturer data which provides the real-time temperature reading as well.

[B]Relevant code snippet:

[/B]
```

using Iter = std::vector<std::unique_ptr<tinyb::BluetoothDevice>>::const_iterator;
while (true)
{
for (Iter it = sensor_tag_array.begin(); it != sensor_tag_array.end(); ++it)
{
std::string address_ = (*it)->get_address();


std::map<uint16_t, std::vector<uint8_t>> mfg__ = (*it)->get_manufacturer_data();
for (auto it : mfg__)
{
if (it.second.empty())
logger_->error("{}, {} :Empty mfg for : {}", __FILENAME__, __func__, bleMap[address_].sensor_name);
else
{
if (it.second.front() == 23)
{
battery_lvl = it.second[1];
first_byte = it.second[6];
second_byte = it.second[7];
temperature = convert_to_actual(first_byte, second_byte) / 10.0;
std::cout << "\nTemperature is for : " << bleMap[address_].sensor_name << " : " << temperature << "\n";
}
}
}
}

```

This was properly giving the correct relatime values until now. But suddenly it started printing a single constant reading each time the application is restarted. Whatever temperature value is first read at application startup is repeated throughout the application runtime. I used the tempo utility app to verify that the sensor is actually reporting the correct realtime values.

I am not able to recollect any changes to the system that could have lead to this issue.

I tried re-installing the OS (Ubuntu 18.04.1), tried multiple version of bluez ( 5.48 which is pre-installed,5.39 and 5.37) but the issue is still there.
I also changed the advertisement frequency in the bluemaestro device.


Then I used "dbus-monitor" to check the packets reported by bluez using the following command:

```

sudo dbus-monitor --system "type='signal',sender='org.bluez'"

```

The output of the command showed that the values being reported by bluez are constant:

```

signal time=1560761344.707933 sender=:1.10 -> destination=(null destination) serial=92 path=/org/bluez/hci0/dev_E7_6A_2D_XX_XX_XX; interface=org.freedesktop.DBus.Properties; member=PropertiesChanged
   string "org.bluez.Device1"
   array [
      dict entry(
         string "ManufacturerData"
         variant             array [
               dict entry(
                  uint16 307
                  variant                      array of bytes [
                        01 b9 03 93 00 d8 01 f8 01 0f 02 b2 00 ed 02 76 01 08
                        02 a3 00 00 00 00 00
                     ]
               )
            ]
      )
   ]
   array [
   ]
signal time=1560761345.837498 sender=:1.10 -> destination=(null destination) serial=93 path=/org/bluez/hci0/dev_E7_6A_2D_XX_XX_XX; interface=org.freedesktop.DBus.Properties; member=PropertiesChanged
   string "org.bluez.Device1"
   array [
      dict entry(
         string "ManufacturerData"
         variant             array [
               dict entry(
                  uint16 307
                  variant                      array of bytes [
                        01 b9 03 93 00 d8 01 f8 01 0f 02 b2 00 ed 02 76 01 08
                        02 a3 00 00 00 00 00
                     ]
               )
            ]
      )
   ]
   array [
   ]
signal time=1560761346.974815 sender=:1.10 -> destination=(null destination) serial=94 path=/org/bluez/hci0/dev_E7_6A_2D_XX_XX_XX; interface=org.freedesktop.DBus.Properties; member=PropertiesChanged
   string "org.bluez.Device1"
   array [
      dict entry(
         string "ManufacturerData"
         variant             array [
               dict entry(
                  uint16 307
                  variant                      array of bytes [
                        01 b9 03 93 00 d8 01 f8 01 0f 02 b2 00 ed 02 76 01 08
                        02 a3 00 00 00 00 00
                     ]
               )
            ]
      )
   ]
   array [
   ]
signal time=1560761348.099627 sender=:1.10 -> destination=(null destination) serial=96 path=/org/bluez/hci0/dev_E7_6A_2D_XX_XX_XX; interface=org.freedesktop.DBus.Properties; member=PropertiesChanged
   string "org.bluez.Device1"
   array [
      dict entry(
         string "ManufacturerData"
         variant             array [
               dict entry(
                  uint16 307
                  variant                      array of bytes [
                        01 b9 03 93 00 d8 01 f8 01 0f 02 b2 00 ed 02 76 01 08
                        02 a3 00 00 00 00 00
                     ]
               )
            ]
      )
   ]
   array [
   ]

```


How to resolve this ?

---

### Post by bluebook2 on 2019-08-14
This may be a dumb question but are you validating the manufacturer code first, to make sure the sensor whose advertisement you are looking at is actually Bluemaestro?  You may be picking up the wrong sensor.

---

