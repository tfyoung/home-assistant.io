---
layout: component
title: "MySensors"
description: "Instructions how to integrate MySensors sensors into Home Assistant."
date: 2015-05-14 21:57
sidebar: true
comments: false
sharing: true
footer: true
logo: mysensors.png
ha_category: Hub
featured: true
---

The [MySensors](https://www.mysensors.org) project combines Arduino boards with NRF24L01 radio boards to build sensor networks. The component will automatically add all available switches and sensors to Home Assistant.

Integrate your Serial MySensors Gateway by adding the following to your `configuration.yaml` file:

```yaml
# Example configuration.yaml entry
mysensors:
  gateways:
    - port: '/dev/ttyUSB0'
      persistence_file: 'path/mysensors.json'
    - port: '/dev/ttyACM1'
      persistence_file: 'path/mysensors2.json'
  debug: true
  persistence: true
  version: '1.5'
```

Configuration variables:

- **port** (*Required*): The port where your board is connected to your Home Assistant host.
- **debug** (*Optional*): Enable or disable verbose debug logging.
- **persistence** (*Optional*): Enable or disable local persistence of sensor information. If this is disabled, then each sensor will need to send presentation messages after Home Assistant starts.
- **persistence_file** (*Optional*): Path to a file to save sensor information. The file extension determines the file type. Currently supported file types are 'pickle' and 'json'.
- **version** (*Optional*): Specifies the MySensors protocol version to use (ex. 1.4, 1.5).

If you are using an original Arduino the port will be named `ttyACM*`. The exact number can be determined with the command shown below.

```bash
$ ls /dev/ttyACM*
```
