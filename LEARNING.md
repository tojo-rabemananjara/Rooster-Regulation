# 16. Test Driven Development with JavaScript

## Write Good Tests with Mocha

*   Rooster Regulation

*   ```javascript
    //index_test.js
    const assert = require('assert');
    const rooster = require('../index');
    
    describe('Rooster', () => {
      describe('.announceDawn', () => {
        it('returns a rooster call', () => {
          //setup
          const expected = 'cock-a-doodle-doo!';
    
          //exercise
          const actual = Rooster.announceDawn();
    
          //verify
          assert.strictEqual(expected, actual);
        });
      });
      describe('.timeAtDawn', () => {
        it('returns its argument as a string', () => {
          //setup
          const expected = '12';
    
          //exercise
          const actual = Rooster.timeAtDawn(12);
    
          //verify
          assert.strictEqual(expected, actual);
        });
        it('throws an error if passed a number less than 0', () => {
          const tooLow = -1;
          assert.throws( () => {
            Rooster.timeAtDawn(tooLow);
          }, RangeError);
        });
    
        it('throws an error if passed a number greater than 23', () => {
          const tooHigh = 24;
          assert.throws( () => {
            Rooster.timeAtDawn(tooHigh);
          }, RangeError);
        });
      });
    });
    ```

*   ```javascript
    //index.js
    // Define a rooster
    Rooster = {};
    
    // Return a morning rooster call
    Rooster.announceDawn = () => {
      return 'cock-a-doodle-doo!';
    }
    
    // Return hour as string
    // Throws Error if hour is not between 0 and 23 inclusive
    Rooster.timeAtDawn = (hour) => {
      if (hour < 0 || hour > 23) {
        throw new RangeError;
      } else {
        return hour.toString();
      };
    }
    
    module.exports = Rooster;
    ```

*   