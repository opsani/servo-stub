# servo-stub
Stub for an Optune adjust driver

This driver returns state base on a configuration file or previously saved state (save from an adjust operation)

Note: this driver requires `adjust.py` base class from the Optune servo core. It can be copied or symlinked here as part of packaging

# driver configuration

The following parameters can be configured for the driver. The configuration should be in a file named `config.yaml` in the same directory as the driver.

* `save_state`: If set to `True`, adjust-ed state would be saved and returned on next query, otherwise, the content of `initial_state` will be returned every time. State will be saved in a file called `stub.state`. Default: `True`
* `initial_state`: State to be returned when `save_state` is `False` or when state file is not present

Example `config.yaml`:

```
stub:
    # If set to True, adjust-ed state should be saved and returned on next
    # query, otherwise, the content of `initial_state` will be returned every
    # time. State will be saved in `stub.state`
    # Default: True
    save_state: True

    initial_state: # this will be returned as is on --query
        application:
            components:
                A:
                    settings:
                        cpu:
                            value: 0.25
                        mem:
                            value: 1.0
```


