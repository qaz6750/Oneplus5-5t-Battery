# Oneplus 5/5T Battery Fuel Gauge Driver
- This drive is based on [SurfaceDuo Battery](https://github.com/woa-project/surfacebattery)
- This driver was originally designed for bq27742-G1 Fuel Gauges on SurfaceDuo, which also means that it can work on other devices using the same meter, provided that you delete the manufacturer's block reading code
- The driver uses Microsoft's own firmware to refresh
- This driver enables Windows to get information about the battery packs used in Oneplus 5/5T. It does not provide charging function.

## ACPI Sample

```asl
Device(BAT1)
{
    Name (_HID, "BQ27411")
    Name (_UID, 1)

    Name (_DEP, Package(0x1) {
        \_SB_.I2C7
    })

    Method (_CRS, 0x0, NotSerialized) {
        Name (RBUF, ResourceTemplate () {
            I2CSerialBus(0x55,, 100000, AddressingMode7Bit, "\\_SB.I2C7",,,,)
        })
        Return (RBUF)
    }
}
```
# License

MIT License

Copyright (c) 2022 WOA Project

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
