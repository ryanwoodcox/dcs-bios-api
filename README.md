# DCS BIOS API

Updated with DCSFlightpanels fork of DCS Bios master branch at commit [https://github.com/DCSFlightpanels/dcs-bios/commit/8650d1a775507fe0d24797c3b7e52cb0039fcf1d]

DCS BIOS API is a library that converts the binary export format from [DCS BIOS](https://github.com/DCSFlightpanels/dcs-bios) into JavaScript objects.

```js
const DcsBiosApi = require('dcs-bios-api');

var api = new DcsBiosApi({ logLevel: 'INFO' });

api.on('SC_MASTER_CAUTION_LED', (value) => {
  console.log('Master caution LED is', value ? 'on' : 'off');
});

api.on('ML_MASTER_ARM:1', () => {
  console.log('Master arm light is on');
});

api.on('ML_MASTER_ARM:0', () => {
  console.log('Master arm light is off');
});

api.sendMessage('WEAPONS_MASTER_ARM 1').then(() => {
  console.log('Master arm switch turned on');
});
```

## Controls Browser

To see a list of controls that DCS BIOS can interact with, checkout the controls browser here: https://danieltian.github.io/dcs-bios-api. Some controls are not available in DCS BIOS. For example, closing the cockpit door is not, and neither are the throttle levers on the Ka-50.
