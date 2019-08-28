# Requirements

- Cython >= 0.27
- libfprint == 0.7.0

# Install

```
pip install git+https://github.com/gtors/fprint#egg=fprint-0.1
```

# Usage

```python
import fprint

fprint.init()
ddevs = fprint.DiscoveredDevices()
if len(ddevs) > 0:
    ddev = ddevs[0]
    dev = fprint.Device.open(ddev)
    (print_data, image) = dev.enroll_finger()
    print_data = fprint.PrintData.from_data(print_data.data)
    (result, img) = dev.verify_finger(print_data)
    assert result is True
    dev.close()
```
